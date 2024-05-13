FROM python:3.10.12
ENV TZ America/Porto_Velho

#Copiando os arquivos necessários
WORKDIR /app
COPY scripts /app/scripts
COPY libs /app/libs
COPY src /app/src

#Instalando as dependências
RUN apt update
RUN apt install -y cron
RUN pip install --upgrade pip
RUN pip install -r /app/src/requirements.txt
RUN sh /app/scripts/libs.sh

#Configurando a execução
#Diariamente às 2h
RUN echo "0 2 * * * sh /app/scripts/run_application.sh >> /var/log/app 2>&1" | crontab -

CMD cron -f
