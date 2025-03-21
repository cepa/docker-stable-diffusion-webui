# Docker + Stable Diffusion + AUTOMATIC1111 Web UI

This is a simple Docker setup using docker compose to get Stable Diffusion with AUTOMATIC111 Web UI up and running in seconds. The stack is configured to use all locally available GPUs.

Tested on Ubuntu and it works.
Update the .env file to adjust the directory paths for model and data storage to your own setup.

*Endpoints*
- http://localhost:7860 - Stable Diffusion WebUI

To start the stack simply run:
~~~
docker compose up --build
~~~
