FROM python:3.6.5

ADD . /jupyter_base

WORKDIR /jupyter_base

RUN apt update && apt install -y \
    python3 \
    python3-pip \
    nodejs \
    git

RUN cp /usr/bin/nodejs /usr/bin/node

RUN pip3 install -i https://pypi.tuna.tsinghua.edu.cn/simple .

RUN pip3 install -i https://pypi.tuna.tsinghua.edu.cn/simple \
    keras \
    xgboost

RUN jupyter notebook --generate-config

RUN echo "c.NotebookApp.ip='*'" >> ~/.jupyter/jupyter_notebook_config.py \
&& echo 'c.NotebookApp.open_browser = False' >> ~/.jupyter/jupyter_notebook_config.py \
&& echo 'c.NotebookApp.port = 8888' >> ~/.jupyter/jupyter_notebook_config.py \
&& echo "c.NotebookApp.base_project_url = '/root/'" >> ~/.jupyter/jupyter_notebook_config.py \
&& echo c.NotebookApp.tornado_settings = "{ 'headers': { 'Content-Security-Policy': \"frame-ancestors 'self' *\" } }" >> ~/.jupyter/jupyter_notebook_config.py

CMD [ "jupyter", "notebook", "--allow-root", "--notebook-dir=/root/"]

