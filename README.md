# pyinstaller-socketio 
Traceback (most recent call last):
  File "jiemian.py", line 31, in run
    socketio = SocketIO(app,async_mode=gevent, cors_allowed_origins='*')
  File "lib\site-packages\flask_socketio\__init__.py", line 185, in __init__
  File "lib\site-packages\flask_socketio\__init__.py", line 245, in init_app
  File "lib\site-packages\socketio\server.py", line 108, in __init__
  File "lib\site-packages\engineio\server.py", line 130, in __init__
ValueError: Invalid async_mode specified
pyinstaller打包后，运行exe出现上述问题，通过查找原因，通过下述方法解决此报错
# py文件中添加此模块导入
from engineio.async_drivers import gevent
# async_mode指定为gevent，此处为字符串
socketio = SocketIO(app,async_mode='gevent')
# 打包指令
pyinstaller -F jiemian.py  --hidden-import=gevent
