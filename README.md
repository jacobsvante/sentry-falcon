# sentry-falcon

[Falcon web framework](https://falconframework.org/) integration for the [Sentry SDK](https://docs.sentry.io/error-reporting/quickstart/?platform=python).

## Installation

```
pip install sentry-falcon
```

## Setup

```python
import sentry_sdk
import sentry_falcon

sentry_sdk.init(
    '__DSN__',
    integrations=[sentry_falcon.FalconIntegration()],
)
```

## Known limitations

- JSON request body will only be captured if the `falcon.Request.media` attribute has been accessed before sending of the Sentry event.
- Raw request bodies are not captured (the Falcon request stream can only be read once)
- User information must be captured manually (for example via Falcon middleware)
