FROM python:alpine

# Install required packages
RUN apk add --update alpine-sdk
RUN apk add --update git
RUN apk add --update nodejs

# Install Jupyter
RUN pip install jupyter
RUN pip install ipywidgets
RUN jupyter nbextension enable --py widgetsnbextension

# Install JupyterLab
RUN pip install jupyterlab && jupyter serverextension enable --py jupyterlab

# Install Python Packages & Requirements (Done near end to avoid invalidating cache)
ADD requirements.txt requirements.txt
RUN apk add --update py-matplotlib py-numpy py-pika
RUN pip install -r requirements.txt

# Expose Jupyter port & cmd
EXPOSE 8888
CMD ["jupyter lab"]
