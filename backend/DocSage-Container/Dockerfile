# Use the official AWS Lambda base image for Python 3.12
FROM public.ecr.aws/lambda/python:3.12

# Copy the requirements file into the container
COPY requirements.txt ${LAMBDA_TASK_ROOT}

# Install all dependencies (no platform flags needed!)
RUN pip install -r requirements.txt

# Copy your function code into the container
COPY main.py ${LAMBDA_TASK_ROOT}

# Set the command to point to your handler (file.function)
CMD [ "main.handler" ]