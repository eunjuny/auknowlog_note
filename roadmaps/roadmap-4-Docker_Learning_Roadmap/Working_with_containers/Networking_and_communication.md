# Networking and Communication Quiz
총 6문항 · 정답 3 · 오답 3

## Q1. What does `docker run -p 8080:80 nginx` do?
- A. Exposes the container only inside the container network
  - 해설: Incorrect: publishing makes the service reachable from the host, not just internally.
- B. Creates a new network bridge for the container
  - 해설: Incorrect: port publishing is not the same as creating a network.
- C. Maps container port 8080 to host port 80
  - 해설: Incorrect: the mapping direction is reversed.
- D. Maps host port 8080 to container port 80
  - 해설: Correct: host traffic sent to 8080 is forwarded to container port 80.
❌ 내 답: Maps container port 8080 to host port 80  |  정답: Maps host port 8080 to container port 80
설명: It publishes container port 80 on host port 8080, so traffic sent to the host reaches the container.

## Q2. If a service is published with `-p 127.0.0.1:5000:5000`, who can connect to it from the host?
- A. Any machine on the local network
  - 해설: Incorrect: it is not exposed to the LAN.
- B. Only processes on the host itself
  - 해설: Correct: 127.0.0.1 binds the port to localhost only.
- C. Only the container that published the port
  - 해설: Incorrect: the publishing container is not the only one able to use the port.
- D. Only other containers on the same bridge network
  - 해설: Incorrect: containers use the container network directly, not the host loopback binding.
❌ 내 답: Only the container that published the port  |  정답: Only processes on the host itself
설명: Binding to 127.0.0.1 limits access to the local machine only.

## Q3. When a container port is published to the host, how is inbound host traffic typically routed?
- A. The host must manually change its routing table for each packet
  - 해설: Incorrect: this routing is handled automatically by Docker.
- B. Docker forwards the host port traffic to the container port
  - 해설: Correct: Docker sets up forwarding/NAT from host port to container port.
- C. Traffic is broadcast to all containers on the host
  - 해설: Incorrect: traffic is not broadcast to every container.
- D. The container listens directly on the host interface without forwarding
  - 해설: Incorrect: the container usually does not bind the host interface directly.
✅ 내 답: Docker forwards the host port traffic to the container port
설명: Docker forwards traffic arriving on the host port to the matching container port.

## Q4. By default, how can containers on the same user-defined bridge network communicate with each other?
- A. They cannot communicate unless `--link` is used
  - 해설: Incorrect: `--link` is legacy and not required for basic communication.
- B. They can communicate only through published host ports
  - 해설: Incorrect: host publishing is for host access, not container-to-container communication.
- C. They can communicate directly over the bridge network
  - 해설: Correct: same-network containers have direct network connectivity.
- D. They must use the host network mode
  - 해설: Incorrect: host network mode is not required.
✅ 내 답: They can communicate directly over the bridge network
설명: Containers on the same user-defined bridge network can reach each other directly using container names or IP addresses.

## Q5. What happens to container-to-container communication on the default Docker bridge network?
- A. Containers can only talk if they are in different networks
  - 해설: Incorrect: containers communicate more easily when they are on the same network.
- B. Containers are not automatically discoverable by name on the default bridge
  - 해설: Correct: automatic name-based discovery is not provided on the default bridge in the same way as user-defined networks.
- C. Every container shares the host IP address
  - 해설: Incorrect: containers do not all share the host IP address.
- D. All containers can resolve each other by name automatically
  - 해설: Incorrect: name resolution is not automatic there.
✅ 내 답: Containers are not automatically discoverable by name on the default bridge
설명: Containers on the default bridge are isolated unless ports are published or additional networking is configured.

## Q6. On a user-defined Docker network, how can one container usually reach another by name?
- A. By editing `/etc/hosts` manually in every container
  - 해설: Incorrect: manual host file edits are not normally needed.
- B. By using the host machine's public IP address
  - 해설: Incorrect: the host's public IP is unrelated to internal container discovery.
- C. By using the other container's name as a hostname
  - 해설: Correct: Docker DNS resolves container names on user-defined networks.
- D. By connecting only through `localhost`
  - 해설: Incorrect: `localhost` refers to the current container, not another one.
❌ 내 답: By using the host machine's public IP address  |  정답: By using the other container's name as a hostname
설명: Docker provides built-in DNS-based service discovery on user-defined networks.