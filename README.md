Testing tool
============


This simple app tests memory leak problem which seems to occur when using flask-socketio + (eventlet, gevent) when
incomming ws connection gets refused (for example because user is denied). It seems that memory usage on server grows.

This tool provides easy setup to see that live.


Installation
------------

Create some virtualenv for the project (for example using virtualenvwrapper: mkvirtualenv flask-ws).

Then in this directory:

`make req_install` will install all needed packages. By default it will use eventlet, but you can change that by
commenting out eventlet in `requirements.in` and uncommented either `gevent` or `gevent-websocket`.


Test
----

`make run` will start flask server at port 5000.

Open it in the browser. You can start test at given intervals between reconnections and stop it.

Run `./watch_memory.sh` which will just filter some lines from `ps`.

On my machine at reconnection rate set to 100 ms I can see that every few seconds memory consumption of python app.py
grows.
