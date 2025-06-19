# LoadBalancer: Smart Traffic Optimization (https://www.youtube.com/watch?v=dI8UkBEBBmg)

A high-performance network traffic management system that optimizes server resource utilization and request processing.

## Problem Solved

Inefficient server load distribution leads to performance bottlenecks, uneven resource allocation, and potential service disruptions during high-traffic scenarios.

## Architecture

![Architecture](https://github.com/ashwin1596/load_balancer/blob/main/Architecture.png)

- Shortest Queue Load Balancing
- Concurrent Client-Server Model
- Scalable Request Handling

## User Impact

- Efficient traffic distribution using Shortest Queue Strategy
- Concurrent handling of multiple client connections
- Reduced server response times
- Improved overall system reliability

## Key Skills Demonstrated

- Object-Oriented Programming (OOP)
- Socket Programming
- Concurrent Programming
- UDP Protocol Implementation
- Python Development

## Key Components

### Load Balancer (`loadbalancer.py`)
- Implements the Shortest Queue Strategy
- Handles request distribution
- Manages server connections

### Controller (`controller.py`)
- Monitors server health
- Manages server pool
- Implements load balancing logic

### Server (`server.py`)
- Processes client requests
- Maintains request queue
- Reports health status

### Client (`client.py`)
- Sends requests to load balancer
- Handles responses
- Implements retry logic

### Models
- **ClientRequest**: Structure for client requests
- **ClientResponse**: Format for responses to clients
- **ControllerRequest**: Internal control messages
- **ServerResponse**: Server status and health updates

## Configuration

The `config.json` file contains all system settings:

```json
{
  "server": {
    "count": "1",
    "port_range_start": "50000",
    "port_range_end": "51000",
    "start_id": "0",
    "queue_update_interval": "10"
  },
  "client": {
    "count": "10",
    "port_range_start": "51000",
    "port_range_end": "52000",
    "start_id": "1000"
  },
  "load_balancer": {
    "server_side_port": "54000",
    "client_side_port": "54001",
    "server_scaling_threshold": "5"
  },
  "controller": {
    "port": "55000"
  }
}
```

## Installation

1. **Clone the repository**
```bash
git clone https://github.com/your-username/load-balancer.git
cd load-balancer
```

2. **Set up virtual environment**
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. **Install dependencies**
```bash
pip install -r requirements.txt
```

## Usage

### Starting the System

1. **Start the Load Balancer**
```bash
python loadbalancer.py
```

2. **Start the Controller**
```bash
python controller.py
```

3. **Launch Servers**
```bash
python server.py --port 8081
python server.py --port 8082
```

4. **Run Test Client**
```bash
python client.py --requests 100
```

## Logging

Logs are organized in three directories:
- `logs/clients/`: Client operation logs
- `logs/controller/`: System control logs
- `logs/servers/`: Individual server logs

## Project Structure

```
.
├── client.py              # Client implementation for sending requests
├── config.json           # Configuration settings for the system
├── controller.py         # Controller logic for managing load balancing
├── loadbalancer.py       # Main load balancer implementation
├── server.py            # Server implementation for handling requests
├── README.md            # Project documentation
├── logs/                # Log files directory
│   ├── clients/         # Client-specific logs
│   ├── controller/      # Controller operation logs
│   └── servers/         # Server-specific logs
└── model/               # Data models
    ├── ClientRequest.py    # Client request model
    ├── ClientResponse.py   # Client response model
    ├── ControllerRequest.py # Controller request model
    └── ServerResponse.py   # Server response model
```
