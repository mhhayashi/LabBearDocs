## Install Instructions

1. Install python 3
2. Create new folder for software
3. Download .whl file from releases into new folder
4. Open command line
5. cd into directory
6. Optional (recommended): Use a virtual environment copying packages from global. (warning: disk space)

Windows
```
pip freeze > requirements.txt
python -m venv .venv
.venv/Scripts/activate
pip install -r requirements.txt
```
Windows may complain about script execution policy. Here are the commands to enable and then disable again script execution:
```
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```
```
Set-ExecutionPolicy -ExecutionPolicy Undefined -Scope CurrentUser
```

Unix
```
pip3 freeze > requirements.txt
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```
7. Install
```
pip install \[LabBear\].whl
```

8. Populate .venv/var/LabBearApp-instance with hardware_config.yml and drivers folder (see repo instance folder for examples)
9. Run: flask --app LabBearApp run

## run this every time
source .venv/bin/activate

## launch the app
flask --app LabBearApp run --debug \[--host IP]
