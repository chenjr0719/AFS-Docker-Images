FROM chenjr0719/afs-docker-images:openpai-deepo

# uninstall tensorflow-gpu
RUN pip uninstall tensorflow-gpu -y

# install afs
RUN pip install --index-url http://124.9.14.99:8080 --trusted-host 124.9.14.99 afs==2.1.8 

# install Jupyter
RUN pip install https://github.com/owen198/notebook/raw/master/dist/notebook-5.6.0.dev0-py2.py3-none-any.whl \
    ipykernel==4.9.0 \
    ipython==6.5.0 \
    ipython_genutils==0.2.0 \
    ipywidgets==7.4.0 \
    jupyter==1.0.0 \
    jupyter_client==5.2.3 \
    jupyter_console==5.2.0 \
    jupyter_core==4.4.0 \
    nbconvert==5.3.1 \
    tornado==4.2 \
    nbformat==4.4.0

# install requirements
RUN pip install tensorflow \
    Deprecated==1.2.3 \
	click==7.0 \
	influxdb==5.2.0 \
	wrapt==1.10.11
