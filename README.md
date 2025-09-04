![Langflow logo](/docs/static/logo/langflow-logo-color-black-solid.svg)

# Langflow Quick Start 🚀

This repository provides instructions and resources for quickly getting started with Langflow, including methods to use Langflow with docling for enhanced document processing capabilities.

---

## 🤖 What is Langflow?

Langflow is an open-source, low-code tool designed for visually constructing interactive workflows using large language models (LLMs). It simplifies the creation and testing of complex AI workflows, chatbots, and data pipelines without extensive coding.

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

### Method 2: Setup with Docker including Docling + User Management

This option enables Langflow's user management. A superuser will be created using the credentials from your `.env`.

**Step 1:** Navigate to the docker_example directory:

```bash
cd docker_example
```

**Step 2:** Clone the .env.example file and rename it to .env:

```bash
cp .env.example .env
```

**Step 3:** Update values in `.env` (change defaults!):
- `POSTGRES_USER`, `POSTGRES_PASSWORD`, `POSTGRES_DB`
- `LANGFLOW_SUPERUSER`, `LANGFLOW_SUPERUSER_PASSWORD` (used on first run to create the superuser)

Optional: Pin a specific Langflow version as in Method 1 before building:

```bash
export LANGFLOW_VERSION=1.5.0
```

**Step 4:** Build and start with the user-enabled Compose file:

```bash
docker compose -f docker-compose-user.yml build && docker compose -f docker-compose-user.yml up -d
```

**Step 5:** Access and sign in:
- Open: http://localhost:7860
- Sign in using the superuser credentials you set in `.env`

### Method 3: Setup with `uv` (Alternative)
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

## 📂 Included Templates

This repository includes pre-built templates in JSON format, which you can directly import into Langflow:
- RAG Agent Example

**To import these templates:**
1. Open Langflow in your browser
2. Create a new empty project  
3. Simply drag and drop the JSON template files directly into your browser window

The templates will be automatically imported and ready to use!

---

## 💻 Use Templates in Code

```python
from langflow import load_flow_from_json

flow = load_flow_from_json("path/to/flow.json")
# Now you can use it like any chain
flow("Hey, have you heard of LangFlow?")
```

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


