FROM public.ecr.aws/lambda/python:3.12

# 1. Install dependencies first (better for caching)
COPY requirements.txt ${LAMBDA_TASK_ROOT}
RUN pip install --no-cache-dir -r requirements.txt

# 2. Copy the files directly into the root
# Note the dot at the end - this copies contents, not the folder itself
COPY . ${LAMBDA_TASK_ROOT}/

# 3. Explicitly set the path to include the task root
ENV PYTHONPATH="${PYTHONPATH}:${LAMBDA_TASK_ROOT}"

# 4. Use the direct file name for the handler
# If your file is main.py and the FastAPI instance is named 'app', use this:
CMD [ "main.handler" ]