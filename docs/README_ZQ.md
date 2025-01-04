# YouTube-DL Audio API

An pythonic RESTful API for getting URL of YouTube videos with only audio or video+audio, perfect for playing in background reducing the network bandwith. Uses [yt-dlp][1] for the queries, and [Flask][2] for the web microframework.

## Usage

To see the full JSON response, you can use the following command:

```bash
curl -s http://localhost:5000/api/0RLvtm0EghQ | python -m json.tool
```

or using PowerShell:
```powershell
curl http://localhost:5000/api/0RLvtm0EghQ | ConvertFrom-Json | ConvertTo-Json -Depth 10
```

## Scalability

The app can be scalated using `gunicorn -c gunicorn_config.py ytdl_audio_api.wsgi`. Is configured to use `gevent` for asynchronous serving.

You can deploy the app to [Heroku][4] or into a [Docker][3] environment.

> **Note**: by default it will use `2 * Cores + 1` workers. You can change this using the `WORKERS`
> environment variable. In Heroku this is mandatory, so add a "Config Var" called `WORKERS` and put
> a value of 1 or 2 (if using the free dyno).

## RESTful API

The API is described in the [OpenApi Schema][oas] or in the `/oas.yaml`/`/swagger.yaml` of a deployed service. 

Use <https://editor.swagger.io>, <https://petstore.swagger.io> (filling the URL at the top) or any other Swagger UI instance to see the API and its documentation.

With the spec, you can also generate clients to talk to your own instance on to my public instance.


## Cache
Some request can be cached using Redis. The only thing you must do to use Redis is setting the environment
variable `REDIS` (or `REDIS_URL` useful for Heroku) with the url of the server.

## Logging
The server has logging for some points of functions. To modify the logging level, set `LOGGING_LEVEL` environment variable to the value you want. Valid values are `CRITICAL`, `FATAL`, `ERROR`, `WARNING`, `WARN`, `INFO`, `DEBUG` or `NOTSET`, see [logging][5] from Python.

## Proxy

You can set a proxy with the environment variable `PROXY`. Supported proxy protocols are http, https and socks5.

If you want to use a proxy as a fallback, use `FALLBACK_PROXY`. This will be used if any call to the YT API fails.

## CORS

By default, CORS is set to allow all origins. This can be overriden by defining the environment variable `CORS_ORIGINS` with a comma-separatid list of origins.

## Pretty JSONs

If, for some reason, you want to get the JSONs in a pretty format, set `JSONIFY_PRETTYPRINT_REGULAR` environment variable to `true`.

  [1]: https://github.com/yt-dlp/yt-dlp
  [2]: http://flask.pocoo.org
  [3]: https://docker.com
  [4]: https://heroku.com
  [5]: https://docs.python.org/3/library/logging.html#logging-levels
  [oas]: https://github.com/melchor629/youtubedl-audio-api/blob/master/ytdl_audio_api/oas.yaml
