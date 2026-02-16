# 1. Use a pre-built image with LibreOffice + Python 3.12 already inside
FROM public.ecr.aws/shelf/lambda-libreoffice-base:7.6-python3.12-x86_64

# 2. Set environment variables for Lambda
ENV HOME=/tmp
ENV LD_LIBRARY_PATH=/var/lang/lib:/lib64:/usr/lib64:/var/runtime:/var/runtime/lib:/var/task:/var/task/lib:/opt/lib:/usr/lib64/libreoffice/program

# 3. Copy your project requirements
COPY requirements.txt ${LAMBDA_TASK_ROOT}

# 4. Install your Python dependencies
RUN pip install --no-cache-dir -r requirements.txt

# 5. Copy your application code
COPY . ${LAMBDA_TASK_ROOT}

# 6. Set the handler
CMD [ "main.handler" ]