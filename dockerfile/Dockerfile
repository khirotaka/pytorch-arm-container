ARG PYTHON_VERSION=3.8.8

FROM arm64v8/python:${PYTHON_VERSION}
ARG TORCH_VERSION=1.8.0

RUN apt-get update && apt-get install -y --no-install-recommends \
    git \
    curl && \
    rm -rf /var/lib/apt/lists/*
    
RUN curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py | python -
ENV PATH=${PATH}:"/root/.poetry/bin"

RUN poetry config virtualenvs.create false && \
    pip install -U pip && \
    pip install torch==${TORCH_VERSION} -f https://download.pytorch.org/whl/torch_stable.html && \
    pip cache purge
    
WORKDIR /workspace
RUN chmod -R a+w .
ENTRYPOINT ["/bin/bash"]
