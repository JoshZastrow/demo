### project folder exactly as I have it localled. Steps to recreate bug below:

```$ cd demo```

#### Initiate Virtual Environment (Windows below, else source myEnv/Scripts/activate)
```$ appEnv\Scripts\activate.bat```

```$ python -V``` <- should be python 3.6

#### if the environment doesn't work:
```$ python -m venv appEnv``` 

```(appEnv) $ python -m pip install pip==9.0.1 flask zappa ```

#### test locally
cmd window 1:

```python my_app.py```

cmd window 2:

```$ curl localhost:5000```

output: 

```$ Hello Flask! ```

#### deploy

```(appEnv) $ zappa deploy dev ```

#### Test (Where Bug Occurs)

```(appEnv) $ curl <insert deployed lambda handle> ```

## To run without bug:

delete **"slim_handler": True** from zappa_settings.json

```(appEnv) $ zappa undeploy dev ```

```(appEnv) $ zappa deploy dev ```
