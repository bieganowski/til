## Default settings in Django pluggable app

< app_name >/__init__.py
```
from django.apps import AppConfig as BaseAppConfig


class AppConfig(BaseAppConfig):
    """
    App's docsring
    """

    name = 'project.app_name'
    label = 'app_label'

    def ready(self):
        from django.conf import settings
        from geosk.auth0 import settings as defult_settings

        # load default settings
        for name in dir(defult_settings):
            if name.isupper() and not hasattr(settings, name):
                # if setting is not present in settings, update settings with it
                setattr(settings, name, getattr(defult_settings, name))

default_app_config = 'app_name.AppConfig'
```