# Simiki Docker

## Building the Docker image

From this repository run:

```
docker build -t simiki .
```

## Using the Docker image

You can simply pass Simiki commands to the Docker `run` command.
For a full list of commands see the Simiki Quick Start guide and documentation:

- Quick Start guide: http://simiki.org/docs/usage.html
- Usage Documentation: http://simiki.org/docs/usage.html

### Initializing a new wiki

```
docker run --rm -it -v $(PWD)/wiki:/wiki simiki init
```

### Generate wiki pages

```
docker run --rm -v $(PWD)/wiki:/wiki simiki g
```

Note: You probably need to pass the timezone via an environment variable e.g.
by adding `-e TZ=UTC`. This prevents an `UnknownTimeZoneError(zone)`
exception (`pytz.exceptions.UnknownTimeZoneError: 'local'`) when
generating the pages.

### Preview/Show the wiki

```
docker run -v $(PWD)/wiki:/wiki -p 8000:8000 simiki p --host 0.0.0.0
```
