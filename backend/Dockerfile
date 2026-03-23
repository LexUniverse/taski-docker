FROM python:3.12-slim

WORKDIR /app

# Создаём pip.conf с зеркалом для всех команд
RUN mkdir -p /root/.pip && \
    echo "[global]" > /root/.pip/pip.conf && \
    echo "index-url = https://pypi.tuna.tsinghua.edu.cn/simple/" >> /root/.pip/pip.conf && \
    echo "trusted-host = pypi.tuna.tsinghua.edu.cn" >> /root/.pip/pip.conf && \
    echo "timeout = 120" >> /root/.pip/pip.conf

RUN pip install gunicorn==23.0.0

COPY requirements.txt .
RUN pip install -r requirements.txt --no-cache-dir

COPY . .

CMD ["gunicorn", "--bind", "0.0.0.0:8000", "backend.wsgi"]
