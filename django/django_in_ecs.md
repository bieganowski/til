## Django in AWS ECS

In oredr to deploy django in AWS ECS, the health check endpoint is required, which may be blocked by a lack of entry 
in `ALLOWED_HOSTS`, since ECS containers are deployed with dynamic IPs.

- the simplest way to solve this is to attach the following to the `ALLOWED_HOSTS`:
    ```python
    from socket import gethostname, gethostbyname 
    ALLOWED_HOSTS = [ gethostname(), gethostbyname(gethostname()), ] 
    ```

- another solution may include https://pypi.org/project/django-allow-cidr/ to define IP range defined in the VPC which
runs the ECS.