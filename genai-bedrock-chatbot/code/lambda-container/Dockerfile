FROM public.ecr.aws/lambda/python:3.11@sha256:58834a0d4d7f86326b6c91d516c66fbe8e91ccd3646ceba4025a66a7a8906e81
RUN yum update --security -y && yum clean all
COPY requirements.txt ${LAMBDA_TASK_ROOT}/
RUN pip3 install -r requirements.txt --no-cache-dir
COPY . ${LAMBDA_TASK_ROOT}
CMD ["genai_chatbot.lambda_handler"]
USER 1001
HEALTHCHECK --interval=600s --timeout=2s --retries=12 \
    CMD ["cat", "requirements.txt"]