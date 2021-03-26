# Streamlit-Docker-Pi
Raspberry Pi, Docker, Streamlit, Poetry

Was having a hard time deploying Streamlit to the Pi4, decided to give docker a try. Takes about 50minutes on a Pi4 to initially build.

### Install:
* git clone this repo
* docker-compose up --build
> Wait, then continue to wait, finally still wait...
* Visit your Pi's IP address (e.g. 192.168.1.11:8501)
* Profit 

### Future updates could include:
* Multi-Stageing to reduce overall size
* /Wheel/ to reduce rebuild time
* .Venv.. Maybe.. Because.. Pi

### Tested on
* Arm8/Arm7 DietPi Pi4 8gb
* Docker 19.03.0+
