## Install Instructions

1. Install python 3
2. Create new folder for software
4. Download .whl file from releases into new folder
5. Open command line
6. cd into directory
7. Install

Option 1 (recommended): Use a virtual environment copying packages from global. (warning: disk space)
```
pip3 freeze > requirements.txt
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```
```
pip install \[LabBear\].whl
```

Option 2: Install globally
```
pip install \[LabBear\].whl
```

12. Populate .venv/var/LabBearApp-instance with hardware_config.yml and drivers folder (see repo instance folder for examples)
13. Run: flask --app LabBearApp run

## run this every time
source .venv/bin/activate

## launch the app
flask --app LabBearApp run --debug \[--host IP]
