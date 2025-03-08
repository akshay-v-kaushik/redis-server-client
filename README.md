# Redis Server-Client

This project consists of a custom Redis server clone deployed on Kubernetes (using k3s and Helm) and a corresponding client that runs locally.

---

## Dependencies

- **Kubernetes (k3s):** Lightweight Kubernetes for deploying the server.
- **Helm:** For deploying and managing the server on Kubernetes.
- **GCC:** For compiling the client application.
- **Git:** For version control and cloning the repository.

---

## Setup Instructions

### 1. Deploy the Server Using Helm

1. **Clone the Repository:**

   ```bash
   git clone https://github.com/akshay-v-kaushik/redis-server-client.git
   cd redis-server-client/redis-clone-chart
   ```

2. **Deploy the Helm Chart:**

   The Helm chart is configured to use the pre-built server image available on Docker Hub. Install the release by running:

   ```bash
   helm install redis-server-clone ./redis-clone-chart
   ```

3. **Verify the Deployment:**

   ```bash
   kubectl get pods
   kubectl get svc
   ```

---

## 2. Compile the Client

1. **Navigate to the Client Directory:**

   ```bash
   cd ../client
   ```

2. **Compile the Client:**

   ```bash
   g++ -Wall -Wextra -O2 -g 11_client.cpp -o client
   ```

---

## 3. Running the Client

Since the client connects to `127.0.0.1:1234`, use port-forwarding to access the server deployed in Kubernetes.

1. **Set Up Port-Forwarding:**

   In a terminal, run:

   ```bash
   kubectl port-forward svc/<svc-name> 1234:1234
   ```

   This command forwards your local port 1234 to the server's port 1234 in the Kubernetes cluster.

2. **Run Client Commands:**

   Open another terminal and execute commands as you normally would. For example:

   ```bash
   ./client set name john
   ./client get name
   ```

   These commands will communicate with the server through the port-forwarding tunnel.

---

