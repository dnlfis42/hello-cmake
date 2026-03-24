# hello-cmake

Ubuntu 24.04 LTS에서 CMake + Ninja로 빌드하는 C++ Hello World 프로젝트

## 개발 환경 세팅

### 필수 패키지 설치

```bash
sudo apt update
sudo apt install build-essential cmake ninja-build valgrind clang-tidy clang-format libgtest-dev -y
```

### Docker 설치

```bash
sudo apt install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

sudo tee /etc/apt/sources.list.d/docker.sources <<EOF
Types: deb
URIs: https://download.docker.com/linux/ubuntu
Suites: $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}")
Components: stable
Signed-By: /etc/apt/keyrings/docker.asc
EOF

sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
sudo usermod -aG docker $USER
newgrp docker
```

### VS Code 확장 설치

```bash
code --install-extension ms-vscode.cpptools
code --install-extension ms-vscode.cmake-tools
code --install-extension llvm-vs-code-extensions.vscode-clangd
```

## 빌드

```bash
mkdir build && cd build
cmake .. -G Ninja
ninja
```

## 실행

```bash
./hello
# Hello, CMake!
```
