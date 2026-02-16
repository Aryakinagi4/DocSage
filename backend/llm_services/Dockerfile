# Use the official AWS Lambda Python 3.11 image
FROM public.ecr.aws/lambda/python:3.11

# Copy requirements file to the task root
COPY requirements.txt ${LAMBDA_TASK_ROOT}

# Install requirements using the pre-built wheels
# --no-cache-dir keeps the image size smaller
RUN pip install --upgrade pip && \
    pip install --no-cache-dir -r requirements.txt

# Copy your application code
COPY . ${LAMBDA_TASK_ROOT}

# Set the entry point for the Lambda function
CMD [ "main.handler" ]