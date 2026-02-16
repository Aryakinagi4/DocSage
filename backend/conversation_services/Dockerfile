FROM public.ecr.aws/lambda/python:3.11

# Set the workdir to the Lambda root
WORKDIR ${LAMBDA_TASK_ROOT}

# Install compilers for SciPy/NumPy
RUN yum update -y && \
    yum install -y gcc gcc-c++ python3-devel && \
    yum clean all

# COPY ONLY the contents of the conversation_services folder
# Since you will run the build FROM inside this folder
COPY . .

# Install dependencies
RUN pip install --no-cache-dir -r requirements.txt

# The handler is now just main.handler because main.py is at the root
CMD [ "main.handler" ]