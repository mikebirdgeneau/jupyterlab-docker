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
RUN apk add --update freetype-dev && apk add --update libpng musl-dev gcc pkgconfig zeromq-dev libc-dev libx11-dev
RUN pip install -r requirements.txt

# Expose Jupyter port & cmd
EXPOSE 8888
CMD ["jupyter lab"]
