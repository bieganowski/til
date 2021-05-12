## Django Rest Framework with Many-to-Many Through a table

In order to serialize additional data stored in `through` table, in an example environment:

``` python
from django.db import models

class User(models.Model):
    # ... model definition
    pass
    
class Activity(models.Model):
    attendees = models.ManyToManyField(User, through='ActivityAttendees')
    # ... model definition
    pass

class ActivityAttendee(models.Model):

    class Meta:
        unique_together = ('user', 'activity')

    user = models.ForeignKey(User, ...)
    activity = models.ForeignKey(Activity, ...)
    status = models.CharField(...)
```

the following may be done:

```python
from .models import Activity, User, ActivityAttendee
from rest_framework import serializers


class UserSerializer(serializers.ModelSerializer):
    # ... serializer definition
    pass


class ActivitySerializer(serializers.ModelSerializer):
    class Meta:
        model = Activity
        fields = '__all__'

    attendees = serializers.SerializerMethodField()

    def get_attendees(self, obj):
        """
        Handle Many-To-Many relationship with extra information
        """
        data = []
        for attendee in obj.attendees.all():
            # Note: to use .get() method here, unique_together constraint must be present
            status = ActivityAttendee.objects.get(user=attendee.id, activity=obj.id).status
            data.append({**UserSerializer().to_representation(attendee), 'status': status})

        return data
```

this will return Activity with User data extended with 'status', e.g.:
```
 {
    "id": <activity_id>,
    ... else Activity serializer definition
    "attendees": [
        {
            "id": <user_id>,
            ... else User serializer definition
            "status": "status string 1"
        },
        {
            "id": <user_id>,
            ... else User serializer definition
            "status": "status string 2"
        }
    ]
},
```