FROM python:3.7
ADD . /home/

# Update and upgrade everything
RUN apt-get -y update && \
    apt-get -y upgrade

# Get node and npm
RUN apt-get install curl && \
    curl -sL https://deb.nodesource.com/setup_16.x | bash - && \
    apt-get install nodejs && \
    npm install -g npm@latest

# Build frontend
WORKDIR /home/frontend
RUN npm install && npm rebuild node-sass && npm run build

# Build backend
WORKDIR /home/api
RUN pip install pip --upgrade 
RUN pip install -r /home/requirements.txt
RUN python -m spacy download en_core_web_md
#RUN pip install https://s3-us-west-2.amazonaws.com/ai2-s2-scispacy/releases/v0.4.0/en_core_sci_md-0.4.0.tar.gz
RUN chmod a+x /home/run.sh
