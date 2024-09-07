# whisper_jupyterlab
<b> 
1. whisper를 하기 위해 jupyterlab 준비

C:\>cd project_ai

C:\project_ai>python --version
Python 3.11.0

C:\project_ai>python3 --version
Python 3.12.5

C:\project_ai>

2. JupyterLab 설치
Python이 설치되어 있다면, 다음 단계로 JupyterLab을 설치할 수 있습니다. CMD 창 또는 터미널에서 다음과 같은 명령어를 입력합니다:

``` bash
pip install jupyterlab
```
<b>

C:\project_ai>pip install jupyterlab
[notice] A new release of pip is available: 23.3.2 -> 24.2
[notice] To update, run: python.exe -m pip install --upgrade pip

C:\project_ai>python.exe -m pip install --upgrade pip를 해준다.
      Successfully uninstalled pip-23.3.2
Successfully installed pip-24.2

<b> 
3. JupyterLab 실행
설치가 완료되면, 다음 명령어를 통해 JupyterLab을 시작할 수 있습니다:

```
jupyter lab
```


![1](https://github.com/user-attachments/assets/c5247511-fe39-432b-bafc-35116691bf1e)


<b> jupyter notebook에서 하는방법 chatgpt에서 알려준 내용




















Windows 노트북에서 JupyterLab을 실행하여 오린(Orin) 보드에 설치된 자동차를 제어하려면 몇 가지 설정과 연결 과정이 필요합니다. 여기에는 네트워크 설정, 코드 수정 및 라이브러리 설치가 포함됩니다.

### 1. 네트워크 연결 설정

오린 보드와 노트북 사이에는 네트워크를 통해 연결해야 합니다. 이를 위해 여러 옵션이 있습니다:

- **직접 연결**: 이더넷 케이블을 사용하여 오린 보드와 노트북을 직접 연결할 수 있습니다. 이 방법을 사용하려면, 노트북과 오린 보드에 고정 IP 주소를 설정해야 할 수 있습니다.
- **로컬 네트워크**: 같은 로컬 네트워크(Wi-Fi 또는 유선 네트워크)에 오린 보드와 노트북을 연결합니다. 이 경우, 오린 보드의 IP 주소를 알아내야 합니다. 보통 `ifconfig` (Linux/UNIX) 또는 `ipconfig` (Windows) 명령어를 통해 확인할 수 있습니다.

### 2. SSH 접근 설정

오린 보드에 SSH 서비스를 활성화하고, 노트북에서 오린 보드에 SSH를 통해 접속할 수 있도록 설정합니다. SSH 접근을 통해 터미널 명령을 원격으로 실행하고 파일을 전송할 수 있습니다.

- **SSH 설정**: 오린 보드에서 SSH 서버를 활성화하고, 외부에서 접근 가능하도록 설정합니다.
- **SSH 클라이언트 사용**: Windows에서는 PuTTY 또는 Windows PowerShell을 사용하여 SSH 접근을 할 수 있습니다.

### 3. 코드 실행

노트북에서 실행되는 JupyterLab과 오린 보드에 있는 하드웨어를 제어하기 위해, 네트워크를 통해 명령을 보내는 코드를 작성해야 합니다. 이를 위해서 Python에서 사용할 수 있는 `paramiko` 같은 라이브러리를 사용하여 SSH를 통한 명령 실행이 가능합니다.

```python
import paramiko

def send_command_to_orin(command):
    ip = "오린 보드의 IP 주소"  # 오린 보드의 IP 주소를 입력하세요
    user = "사용자 이름"        # 사용자 이름을 입력하세요
    password = "비밀번호"      # 비밀번호를 입력하세요

    ssh = paramiko.SSHClient()
    ssh.set_missing_host_key_policy(paramiko.AutoAddPolicy())
    ssh.connect(ip, username=user, password=password)
    stdin, stdout, stderr = ssh.exec_command(command)
    print(stdout.read().decode())
    ssh.close()
```

위 함수를 사용하여 오린 보드에서 필요한 명령을 실행할 수 있습니다. 예를 들어, 오린 보드에서 파이썬 스크립트를 실행하려면, 해당 스크립트 파일을 오린 보드에 업로드한 다음, `send_command_to_orin('python3 your_script.py')`와 같이 명령을 호출할 수 있습니다.

### 4. 라이브러리 설치 및 환경 설정

오린 보드에서 필요한 Python 라이브러리와 의존성이 모두 설치되어 있는지 확인하고, 필요한 경우 노트북에서도 동일한 라이브러리를 설치해야 할 수 있습니다.

이 모든 설정을 완료하면, 노트북에서 JupyterLab을 사용하여 오린 보드에 설치된 자동차를 원격으로 제어할 수 있게 됩니다.


















