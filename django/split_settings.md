## Prevent huge settings.py in django with split_settings 

```
pip install django-split-settings
```

- create `conf/` directory in your project ROOT
- create `base` directory & directories for environments there, e.g. `local`, `dev`, `stage`, `prod`
- in directories you can have multiple files
- in `settings.py`:
    ```
    import os
    from split_settings.tools import optional, include
    
    
    PROJECT_ENVIRONMENT = os.getenv("PROJECT_ENVIRONMENT", "prod")
    include(
        "conf/base/*.py", optional(f"conf/{PROJECT_ENVIRONMENT}/*.py"),
    )
    ```

Settings from `base/` will be applied as defaults; from other dirs will overwrite according to `PROJECT_ENVIRONMENT` envvar.

____
##### Cons:
- Pycharm does not redirect to a setting when looking for it's declaration
- easy to mess up by not following the convention