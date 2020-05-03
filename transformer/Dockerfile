FROM continuumio/anaconda3:2020.02

WORKDIR /lab
ADD requirements.txt /lab/
RUN conda install --yes --file requirements.txt

CMD ["jupyter", "notebook", "--allow-root", "--ip=0.0.0.0"]
