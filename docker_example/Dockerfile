ARG LANGFLOW_VERSION=latest
FROM langflowai/langflow:${LANGFLOW_VERSION}

COPY --from=ghcr.io/astral-sh/uv:0.8.3 /uv /uvx /bin/

RUN uv pip install docling

CMD ["python", "-m", "langflow", "run", "--host", "0.0.0.0", "--port", "7860"]
