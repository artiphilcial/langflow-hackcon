![Langflow logo](/docs/static/logo/langflow-logo-color-black-solid.svg)

# Langflow Quick Start 🚀

This repository provides instructions and resources for quickly getting started with Langflow, including methods to use Langflow with docling for enhanced document processing capabilities.

---

## 🤖 What is Langflow?

Langflow is an open-source, low-code tool designed for visually constructing interactive workflows using large language models (LLMs). It simplifies the creation and testing of complex AI workflows, chatbots, and data pipelines without extensive coding.

![Langflow tools](/docs/static/img/tools.png)

Visit [Langflow's GitHub repository](https://github.com/langflow-ai/langflow) and [official website](https://langflow.org/) for more information.

---

## 🛠️ Quick Start

### Prerequisites

#### Packages

- Colima (macOS): `brew install colima && colima start` (required for Method 1)
- uv (required for Method 2)
- Chromium-based browser

#### Credentials

- watsonx API key
- watsonx Project ID

Important: In Langflow, within the Language Model component, select the watsonx API endpoint (region) where your runtime is provisioned (e.g., eu-de, us-south) to ensure successful connections.

### Method 1: Setup with Docker including [Docling](https://github.com/docling-project/docling)

**Step 1:** Navigate to the docker_example directory:

```bash
cd docker_example
```

**Step 2:** Clone the .env.example file and rename it to .env:

```bash
cp .env.example .env
```

**Step 3:** Update your PostgreSQL values in the .env file:

Edit the .env file as needed. The application uses environment variables for configuration:
- `POSTGRES_USER`: The username for the PostgreSQL database (default: langflow)
- `POSTGRES_PASSWORD`: The password for the PostgreSQL database (default: langflow)
- `POSTGRES_DB`: The name of the PostgreSQL database (default: langflow)

**Step 4:** (Optional) Pin a specific Langflow version (default is `latest`):

```bash
export LANGFLOW_VERSION=1.5.0  # omit to use latest
```

**Step 5:** Build and start the container:

```bash
docker compose up -d
```

**Step 6:** Access Langflow:

Open your browser and navigate to: http://localhost:7860 in a Chromium-based browser.


### Method 2: Setup with `uv` (Alternative)
(langflow not included)

**Step 1:** Set up your virtual environment and install Langflow:

```bash
uv pip install langflow
```

**Step 2:** Run Langflow:

```bash
uv run langflow run
```

Open your browser and navigate to: http://localhost:7860 in a Chromium-based browser.

---


## 🔧 Customization

### Switching Langflow Versions

Default is `latest`. To pin a version, set the build arg/env `LANGFLOW_VERSION` before building:

```bash
export LANGFLOW_VERSION=1.5.0
docker compose build --no-cache
docker compose up -d
```

This value is passed to the Docker build and used to tag the resulting image, ensuring the same version is used consistently.

### Environment Variables

The Docker Compose configuration automatically constructs the database connection string from your `.env` file. The application stores logs, file storage, monitor data, and secret keys in the `langflow-data` volume.

---

## 📚 Additional Resources

- [Langflow Documentation](https://docs.langflow.org/)
- [Docling Project](https://github.com/docling-project/docling)
- [Langflow Docker Hub](https://hub.docker.com/r/langflowai/langflow)


