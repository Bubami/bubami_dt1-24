# Retool Integration with GPT-2 API

This project is part of the DT1 2023: Enabling Technologies course, Assignment 1. It showcases the deployment and interaction with the Huggingface Inference API using a Flask-based proxy. The application is integrated with the Retool platform for front-end interaction and supports no-code Bubble for interface building. The project explores various aspects of software architecture, API design, and cloud computing.

---

## Table of Contents

1. [Overview](#overview)
2. [Features](#features)
3. [Getting Started](#getting-started)
   - [Prerequisites](#prerequisites)
   - [Installation](#installation)
   - [Usage](#usage)
4. [API Endpoints](#api-endpoints)
5. [Cloud Deployment](#cloud-deployment)
6. [Troubleshooting](#troubleshooting)
7. [Contributing](#contributing)
8. [License](#license)
9. [Contact](#contact)

---

## Overview

This assignment involves deploying a small Flask application that acts as a proxy to the Huggingface Inference API. The application is containerized using Docker and deployed on Google Cloud Platform (GCP). A no-code Bubble interface is used to interact with the API, demonstrating an end-to-end implementation covering:

- Software Architecture
- API Design
- Cloud Deployment
- No-Code Interface Development

---

## Features

- **Huggingface API Proxy:** Interact seamlessly with the Huggingface Inference API.
- **Dockerized Deployment:** Simplified application setup and deployment.
- **Cloud Integration:** Hosted on GCP for scalability and accessibility.
- **Bubble Integration:** User-friendly no-code interface for API interaction.
- **Customization:** Adjust parameters to optimize responses.

---

## Getting Started

### Prerequisites

Ensure the following before setting up the project:

- **Google Cloud Account:** Required for hosting the application.
- **Huggingface API Access:** Obtain an API token.
- **Docker Installed:** Follow [this guide](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-debian-10).
- **Basic Knowledge of Flask and Docker.**

### Installation

1. **Clone the Repository:**

   ```bash
   git clone https://github.com/username/repository.git
   cd repository
   ```

2. **Install Dependencies:**

   Use `pipenv` to install dependencies locally:

   ```bash
   pipenv install
   pipenv shell
   ```

3. **Build Docker Image:**

   ```bash
   docker build -t gpt2-proxy .
   ```

4. **Run Docker Container Locally:**

   ```bash
   docker run -p 8080:8080 gpt2-proxy
   ```

---

## Usage

1. **API Interaction:**

   Make GET requests to the following endpoint:

   ```plaintext
   http://<your-host>:8080/chat?huggingface_token=<YOUR_TOKEN>&input=<USER_INPUT>&model_id=gpt2
   ```

   Example:

   ```plaintext
   http://34.65.158.210:8080/chat?huggingface_token=hf_exampleToken&input=What%20is%20the%20capital%20of%20France?&model_id=gpt2
   ```

2. **Bubble Integration:**

   Use Bubble to create a user interface for interacting with the API. Define input fields and map them to the API parameters.

---

## API Endpoints

### **GET /chat**

**Description:** Sends a query to the GPT-2 model and retrieves a response.

**Parameters:**

- `huggingface_token` *(Required)*: Your Huggingface API token.
- `input` *(Required)*: Text query for the model.
- `model_id` *(Required)*: Identifier for the GPT-2 model.
- **Optional:**
  - `max_length`: Maximum response length.
  - `temperature`: Sampling temperature.
  - `top_k`: Top-k sampling value.
  - `repetition_penalty`: Penalize repetitive outputs.

**Example Response:**

```json
{
  "ack": "The capital of France is Paris."
}
```

---

## Cloud Deployment

1. **Setup GCP Instance:**

   - Create a Compute Engine instance with Ubuntu (Debian).
   - Configure firewall rules to allow traffic on port `8080`.

2. **Deploy Docker Image:**

   - SSH into the instance.
   - Pull the Docker image from Docker Hub or build it directly.

   ```bash
   docker run -p 8080:8080 gpt2-proxy
   ```

3. **Test Deployment:**

   Access the API at `http://<GCP_INSTANCE_IP>:8080`.

---

## Troubleshooting

### **Common Issues:**

1. **Connection Errors:**
   - Verify that the instance is running and the firewall allows traffic.

2. **Nonsensical Outputs:**
   - Fine-tune `temperature` and `top_k` parameters.

3. **Docker Issues:**
   - Ensure Docker is installed and running on the VM.

### **Debugging Tips:**

- Use `curl` for local API testing.
- Check logs for detailed error messages.

---

## Contributing

Contributions are welcome! Follow these steps:

1. Fork the repository.
2. Create a feature branch:
   ```bash
   git checkout -b feature-branch
   ```
3. Commit your changes:
   ```bash
   git commit -m 'Add feature'
   ```
4. Push your branch:
   ```bash
   git push origin feature-branch
   ```
5. Submit a pull request.

---

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

---

## Contact

For inquiries or support:

- **Name:** Michael Buchbauer
- **Email:** michael@buchbauer.ch   
- **GitHub:** [Bubami](https://github.com/Bubami)

