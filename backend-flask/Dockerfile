FROM python:3.10-slim-buster
# Inside Container
# Make a new folder inside the container
WORKDIR /backend-flask
# Outside Container -> Inside Container
# Contains the libraries we want to install to run the app
COPY requirements.txt requirements.txt
# Inside Container
# Installs the python libraries used for the app 
RUN pip3 install -r requirements.txt
# Outside Container -> Inside Container
# (.)period means everything in the current directory
# the first period(.) means ./backend-flask(outside the container)
# the second period(.) means ./backend-flask(inside the container)
COPY . .

ENV FLASK_ENV=development

EXPOSE ${PORT}
CMD [ "python3", "-m" , "flask", "run", "--host=0.0.0.0", "--port=4567"]