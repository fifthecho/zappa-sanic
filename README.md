# Zappa Sanic Test App

- After adding an S3 bucket, `sanic deploy`
- Once deployed, `curl` the URL deployed to. App should respond like 

```
"{'message': 'An uncaught exception happened while servicing this request. You can investigate this with the `zappa tail` command.', 'traceback': ['Traceback (most recent call last):\\n', '  File \"/var/task/handler.py\", line 457, in handler\\n    response = Response.from_app(self.wsgi_app, environ)\\n', '  File \"/var/task/werkzeug/wrappers.py\", line 903, in from_app\\n    return cls(*_run_wsgi_app(app, environ, buffered))\\n', '  File \"/var/task/werkzeug/test.py\", line 884, in run_wsgi_app\\n    app_rv = app(environ, start_response)\\n', '  File \"/var/task/zappa/middleware.py\", line 66, in __call__\\n    response = self.application(environ, encode_response)\\n', 'TypeError: __call__() takes 1 positional argument but 3 were given\\n']}"
```

- `zappa tail` should log something like 

```
[1494252741172] [DEBUG] 2017-05-08T14:12:21.172Z 59e6e759-33f8-11e7-ba65-ffadf5101311 Zappa Event: {'resource': '/', 'path': '/', 'httpMethod': 'GET', 'headers': {'Accept': '*/*', 'CloudFront-Forwarded-Proto': 'https', 'CloudFront-Is-Desktop-Viewer': 'true', 'CloudFront-Is-Mobile-Viewer': 'false', 'CloudFront-Is-SmartTV-Viewer': 'false', 'CloudFront-Is-Tablet-Viewer': 'false', 'CloudFront-Viewer-Country': 'US', 'Host': '73wzpd7gdj.execute-api.us-east-1.amazonaws.com', 'User-Agent': 'curl/7.54.0', 'Via': '2.0 6ac547ea4fdffc736699ded8bb83b53f.cloudfront.net (CloudFront)', 'X-Amz-Cf-Id': '7Shg6U426ybSXUh75ZxK8f4Ha2mvZxqJ82kK5Z37C53le1Ohw7wmMA==', 'X-Amzn-Trace-Id': 'Root=1-59107cc5-7264ebca105d6ebd30ac31e8', 'X-Forwarded-For': '108.29.95.21, 54.239.145.163', 'X-Forwarded-Port': '443', 'X-Forwarded-Proto': 'https'}, 'queryStringParameters': None, 'pathParameters': None, 'stageVariables': None, 'requestContext': {'path': '/dev', 'accountId': '074567182610', 'resourceId': 'cdut4b7c03', 'stage': 'dev', 'requestId': '59e0cc6c-33f8-11e7-9b10-33f6541ac648', 'identity': {'cognitoIdentityPoolId': None, 'accountId': None, 'cognitoIdentityId': None, 'caller': None, 'apiKey': '', 'sourceIp': '108.29.95.21', 'accessKey': None, 'cognitoAuthenticationType': None, 'cognitoAuthenticationProvider': None, 'userArn': None, 'userAgent': 'curl/7.54.0', 'user': None}, 'resourcePath': '/', 'httpMethod': 'GET', 'apiId': '73wzpd7gdj'}, 'body': None, 'isBase64Encoded': False}
[1494252741172] __call__() takes 1 positional argument but 3 were given
```