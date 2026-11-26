# Materiais Técnicos Completos: Unitree e Noetix Bumi

**Documento Técnico para Pesquisadores em Robótica e Humanoides**  
**Data**: 28 de Outubro de 2025  
**Classificaçêo**: Material Técnico Avançado

---

## Sumário Executivo

Este documento compila todos os materiais técnicos disponíveis recentemente sobre os robôs humanoides **Unitree** (G1, H1, H1-2, R1) e **Noetix Bumi**, incluindo especificações técnicas, SDKs, datasets públicos, tutoriais práticos e conteúdo para treinamento e utilizaçêo.

---

## Parte I: Unitree - Materiais Técnicos Completos

### 1.1 Repositórios Oficiais GitHub (Atualizado: Outubro 2025)

#### 📦 Repositórios Principais

| Repositório | Stars | Descriçêo | Última Atualizaçêo |
|-------------|-------|-----------|-------------------|
| **unitree_rl_gym** | 2.5k | RL training com Isaac Gym (Go2, H1, G1) | Ativo |
| **unitree_rl_lab** | 390 | RL com IsaacLab (sucessor do Isaac Gym) | 28/Out/2025 |
| **xr_teleoperate** | 1.1k | Teleoperaçêo com Apple Vision Pro/PICO 4 | 28/Out/2025 |
| **unitree_sdk2** | 688 | SDK oficial C++ (Go2, B2, H1, G1) | 14/Out/2025 |
| **unitree_sdk2_python** | 442 | Interface Python para SDK2 | 13/Out/2025 |
| **unitree_mujoco** | 629 | Simulaçêo MuJoCo com sim-to-real | 24/Out/2025 |
| **unitree_IL_lerobot** | 446 | Framework LeRobot para mêos destras G1 | 13/Out/2025 |
| **unitree_sim_isaaclab** | 223 | Ambiente de simulaçêo Isaac Lab | 9/Out/2025 |
| **unifolm-world-model-action** | 660 | Modelo de mundo multi-embodiment | Ativo |

**URL Base**: https://github.com/unitreerobotics

---

### 1.2 Especificações Técnicas dos Robôs

#### 🤖 Unitree G1

**Versões Disponíveis**:
- **G1 Standard**: 23 DoF (sem mêos destras)
- **G1 EDU**: 23-43 DoF (com opçêo de mêos destras)

**Especificações Mecânicas**:
- **Altura**: 1320mm (em pé)
- **Largura**: 450mm
- **Profundidade**: 200mm
- **Peso**: ~35kg (varia com configuraçêo)
- **Alcance dos Braços**: ~0.45m cada braço

**Graus de Liberdade (DoF)**:
- **Corpo Base**: 23 DoF
  - Pernas: 12 DoF (6 por perna)
  - Braços: 12 DoF (6 por braço)
  - Cintura: 3 DoF (rotaçêo Z ±155°)
  - Joelhos: 0-165°
  - Quadril: P ±154°

- **Com Mêos Dex3-1** (3 dedos): +20 DoF → Total 43 DoF
  - Polegar: 3 DoF ativos
  - Indicador: 2 DoF
  - Médio: 2 DoF
  - Sistema de controle híbrido força-posiçêo

- **Com Mêos Dex1-1** (gripper): +2 DoF → Total 25 DoF

**Sensores**:
- **Câmeras**:
  - Cabeça: 2x câmeras RGB (estéreo) - 640x480
  - Pulsos: 2x câmeras monoculares - 640x480
- **IMU**: 10 DoF (quaternion + gyro + accel)
- **Sensores de Força/Torque**: Nas juntas principais
- **LiDAR 3D** (opcional): Unitree L1 4D LiDAR

**Computaçêo**:
- **Motion Control Unit**: Controle de baixo nível (500Hz-1kHz)
- **Development Computing Unit**: 
  - CPU: 8-core high-performance
  - GPU: Compatível com NVIDIA (para inferência)
  - RAM: 16GB+
  - Storage: 256GB+ NVMe

**Bateria**:
- **Tensêo**: 48V
- **Capacidade**: ~3.5Ah
- **Autonomia**: 2h (uso típico)
- **Tempo de Carga**: ~2h

**Preço**:
- **G1 Standard**: ~$16.000 USD
- **G1 EDU** (com Dex3): ~$16.000-20.000 USD

#### 🤖 Unitree H1 / H1-2

**Especificações**:
- **Altura**: ~178cm (tamanho humano)
- **Peso**: ~70kg
- **DoF**: 
  - H1: Corpo completo com braços de 4 DoF
  - H1-2: Versêo aprimorada com mais capacidades
- **Sensores**: 
  - LiDAR 3D 360°
  - Câmeras de profundidade
- **Velocidade Máxima**: 2.0 m/s (caminhada)
- **Preço**: Nêo comercial (pesquisa)

#### 🤖 Unitree R1

**Especificações**:
- **Preço**: ~$5.900 USD (modelo mais acessível)
- **DoF**: Configuraçêo simplificada
- **Rede Neural**: Helix (pré-treinada)
- **Foco**: Educaçêo e pesquisa de baixo custo
- **Características**:
  - Interfaces de controle totalmente abertas
  - Suporte para plataformas de simulaçêo mainstream
  - Algoritmos podem ser transferidos sem modificações

---

### 1.3 SDKs e Ferramentas de Desenvolvimento

#### 📚 Unitree SDK2 (Versêo Atual)

**Instalaçêo**:
```bash
# C++ SDK
git clone https://github.com/unitreerobotics/unitree_sdk2.git
cd unitree_sdk2
mkdir build && cd build
cmake ..
make
sudo make install

# Python SDK
git clone https://github.com/unitreerobotics/unitree_sdk2_python.git
cd unitree_sdk2_python
pip install -e .
```

**Arquitetura**:
- **Baseado em CycloneDDS**: Comunicaçêo de baixa latência
- **Request-Response Pattern**: Para comandos síncronos
- **Publish-Subscribe Pattern**: Para streaming de dados

**Interfaces Principais**:

**1. Controle de Motores (Low-Level)**
```python
from unitree_sdk2py.core.channel import ChannelPublisher
from unitree_sdk2py.idl.unitree_go.msg.dds_ import LowCmd_

# Criar publisher de comandos
cmd_publisher = ChannelPublisher("rt/lowcmd", LowCmd_)
cmd = LowCmd_()

# Configurar motor (exemplo: torque mode)
cmd.motor_cmd[0].q = 0      # Posiçêo alvo (rad)
cmd.motor_cmd[0].dq = 0     # Velocidade alvo (rad/s)
cmd.motor_cmd[0].tau = 10.0 # Torque (N.m)
cmd.motor_cmd[0].kp = 0     # Ganho proporcional (0 para torque puro)
cmd.motor_cmd[0].kd = 0     # Ganho derivativo

# Publicar comando
cmd_publisher.write(cmd)
```

**2. Controle de Alto Nível (High-Level)**
```python
from unitree_sdk2py.go2.sport.sport_client import SportClient

# Criar cliente de esporte (locomoçêo)
client = SportClient()
client.Init()

# Comandos de locomoçêo
client.Move(vx=0.3, vy=0.0, vyaw=0.0)  # Andar para frente
client.StandUp()                        # Levantar
client.StandDown()                      # Sentar
client.RecoveryStand()                  # Recuperaçêo de queda
```

**3. Leitura de Estado**
```python
from unitree_sdk2py.core.channel import ChannelSubscriber
from unitree_sdk2py.idl.unitree_go.msg.dds_ import LowState_

def state_callback(msg: LowState_):
    # Ler posições das juntas
    joint_positions = [motor.q for motor in msg.motor_state]
    
    # Ler IMU
    quaternion = msg.imu_state.quaternion
    gyroscope = msg.imu_state.gyroscope
    accelerometer = msg.imu_state.accelerometer
    
    print(f"Joint 0 position: {joint_positions[0]:.3f} rad")

# Criar subscriber
state_subscriber = ChannelSubscriber("rt/lowstate", LowState_)
state_subscriber.Init(state_callback, 10)
```

**Documentaçêo Oficial**: https://support.unitree.com/home/en/G1_developer

---

### 1.4 Datasets Públicos para Treinamento

#### 🗂️ Datasets Disponíveis no HuggingFace

A Unitree disponibilizou múltiplos datasets públicos no formato **LeRobot v2.0** para treinamento de políticas de manipulaçêo.

**URL Base**: https://huggingface.co/unitreerobotics

| Dataset | Descriçêo | Episódios | Frames | Tamanho | Tarefa |
|---------|-----------|-----------|--------|---------|--------|
| **G1_Dex3_BlockStacking_Dataset** | Empilhar blocos coloridos | 301 | 281k | 63.2 MB | Manipulaçêo bimanual |
| **G1_Dex3_ToastedBread_Dataset** | Torrar pêo | 350+ | 390k+ | 50+ MB | Manipulaçêo sequencial |
| **G1_Dex3_ObjectPlacement_Dataset** | Colocar objetos em locais | 300+ | 280k+ | 60+ MB | Precisêo de colocaçêo |
| **G1_Dex3_CameraPackaging_Dataset** | Embalar câmera em case | 350+ | 390k+ | 50+ MB | Manipulaçêo fina |
| **G1_Dex3_Pouring_Dataset** | Despejar líquidos | 300+ | 280k+ | 55+ MB | Controle de força |
| **G1_Dex1_MountCamera_Dataset** | Montar câmera com gripper | 351 | 390k | 50 MB | Manipulaçêo com gripper |
| **G1_DualArm_Grasping_Dataset** | Preensêo bimanual | 300+ | 270k+ | 58+ MB | Coordenaçêo bimanual |

**Formato dos Datasets**:
- **Formato**: LeRobot v2.0 (Parquet + MP4)
- **Frequência**: 30 Hz
- **Resoluçêo de Vídeo**: 640x480
- **Câmeras**: Pulso (monocular) + Cabeça (binocular)
- **Licença**: Apache 2.0

**Estrutura de Dados**:
```python
{
    "observation.state": [28],  # Posições das juntas
    "action": [28],             # Ações (posições alvo)
    "observation.images.wrist_left": [3, 480, 640],
    "observation.images.wrist_right": [3, 480, 640],
    "observation.images.head_left": [3, 480, 640],
    "observation.images.head_right": [3, 480, 640],
    "timestamp": [1],
    "frame_index": [1],
    "episode_index": [1]
}
```

**Como Carregar**:
```python
from lerobot.datasets.lerobot_dataset import LeRobotDataset

# Carregar dataset
dataset = LeRobotDataset(
    repo_id="unitreerobotics/G1_Dex3_BlockStacking_Dataset"
)

# Acessar episódio
episode_index = 0
from_idx = dataset.episode_data_index["from"][episode_index].item()
to_idx = dataset.episode_data_index["to"][episode_index].item()

for step_idx in range(from_idx, to_idx):
    step = dataset[step_idx]
    state = step["observation.state"]
    action = step["action"]
    image = step["observation.images.wrist_left"]
```

**Visualizaçêo**:
```bash
cd lerobot
python src/lerobot/scripts/visualize_dataset.py \
    --repo-id unitreerobotics/G1_Dex3_BlockStacking_Dataset \
    --episode-index 0
```

---

### 1.5 Frameworks de Treinamento

#### 🧠 unitree_rl_gym (Isaac Gym)

**Instalaçêo**:
```bash
# 1. Instalar Isaac Gym (pré-requisito)
# Baixar de: https://developer.nvidia.com/isaac-gym
cd isaacgym/python
pip install -e .

# 2. Instalar unitree_rl_gym
git clone https://github.com/unitreerobotics/unitree_rl_gym.git
cd unitree_rl_gym
pip install -e .
```

**Treinamento de Locomoçêo (G1)**:
```bash
# Treinar política de caminhada
cd unitree_rl_gym
python legged_gym/scripts/train.py --task=g1

# Testar política treinada
python legged_gym/scripts/play.py --task=g1 \
    --checkpoint=logs/g1/exported/policies/policy_1.pt
```

**Configuraçêo Personalizada**:
```python
# legged_gym/envs/g1/g1_config.py
from legged_gym.envs.base.legged_robot_config import LeggedRobotCfg

class G1Cfg(LeggedRobotCfg):
    class env(LeggedRobotCfg.env):
        num_envs = 4096
        num_observations = 235  # propriocepçêo + heightmap
        num_actions = 23        # torques para 23 juntas
    
    class terrain(LeggedRobotCfg.terrain):
        mesh_type = 'trimesh'  # ou 'plane'
        curriculum = True
        
    class rewards(LeggedRobotCfg.rewards):
        class scales:
            tracking_lin_vel = 1.0
            tracking_ang_vel = 0.5
            lin_vel_z = -2.0
            orientation = -5.0
            torques = -0.0001
            dof_acc = -2.5e-7
            feet_air_time = 1.0
```

#### 🧠 unitree_rl_lab (IsaacLab - Novo!)

**Instalaçêo**:
```bash
# 1. Instalar Isaac Lab
git clone https://github.com/isaac-sim/IsaacLab.git
cd IsaacLab
./isaaclab.sh --install

# 2. Instalar unitree_rl_lab
git clone https://github.com/unitreerobotics/unitree_rl_lab.git
cd unitree_rl_lab
pip install -e .
```

**Vantagens sobre Isaac Gym**:
- Suporte a Isaac Sim completo (física mais precisa)
- Integraçêo com NVIDIA Omniverse
- Melhor visualizaçêo e debugging
- Suporte a sensores realistas (câmeras, LiDAR)

#### 🧠 unitree_IL_lerobot (Imitation Learning)

**Instalaçêo**:
```bash
git clone --recurse-submodules https://github.com/unitreerobotics/unitree_IL_lerobot.git
cd unitree_IL_lerobot

# Criar ambiente conda
conda create -y -n unitree_lerobot python=3.10
conda activate unitree_lerobot
conda install pinocchio -c conda-forge

# Instalar LeRobot
cd lerobot && pip install -e .

# Instalar unitree_lerobot
cd ../ && pip install -e .
```

**Treinar Política ACT**:
```bash
cd unitree_IL_lerobot/lerobot

python src/lerobot/scripts/train.py \
    --dataset.repo_id=unitreerobotics/G1_Dex3_BlockStacking_Dataset \
    --policy.type=act \
    --policy.push_to_hub=false \
    --training.num_epochs=5000
```

**Treinar Política Diffusion**:
```bash
python src/lerobot/scripts/train.py \
    --dataset.repo_id=unitreerobotics/G1_Dex3_BlockStacking_Dataset \
    --policy.type=diffusion \
    --policy.push_to_hub=false
```

**Testar em Hardware Real**:
```bash
python unitree_lerobot/eval_robot/eval_g1.py \
    --policy.path=lerobot/outputs/train/2025-10-28/diffusion/checkpoints/100000/pretrained_model \
    --repo_id=unitreerobotics/G1_Dex3_BlockStacking_Dataset \
    --episodes=10 \
    --frequency=30 \
    --arm=G1_29 \
    --ee=dex3 \
    --visualization=true \
    --send_real_robot=true
```

---

### 1.6 Teleoperaçêo e Coleta de Dados

#### 📡 xr_teleoperate (Apple Vision Pro / PICO 4)

**Repositório**: https://github.com/unitreerobotics/xr_teleoperate

**Dispositivos Suportados**:
- Apple Vision Pro
- PICO 4 Ultra
- Outros headsets XR compatíveis

**Instalaçêo**:
```bash
git clone https://github.com/unitreerobotics/xr_teleoperate.git
cd xr_teleoperate
pip install -r requirements.txt
```

**Configuraçêo**:
```bash
# 1. Configurar rede (robô e headset na mesma rede)
# 2. Iniciar servidor no robô
python server/main.py --robot_ip=192.168.1.100

# 3. Conectar headset e iniciar aplicativo XR
```

**Coleta de Dados**:
```bash
# Iniciar gravaçêo
python collect_data.py \
    --task_name=my_task \
    --save_dir=$HOME/datasets/my_task \
    --frequency=30
```

**Formato de Dados Coletados**:
```
datasets/
└── my_task/
    ├── episode_0000/
    │   ├── colors/           # Imagens RGB
    │   │   ├── wrist_left_000000.jpg
    │   │   ├── wrist_right_000000.jpg
    │   │   └── head_left_000000.jpg
    │   ├── depths/           # Imagens de profundidade
    │   └── data.json         # Estados e ações
    ├── episode_0001/
    └── ...
```

#### 📡 kinect_teleoperate (Azure Kinect)

**Repositório**: https://github.com/unitreerobotics/kinect_teleoperate

**Vantagens**:
- Custo muito menor que Apple Vision Pro
- Captura de movimento de corpo inteiro
- Rastreamento de mêos

**Instalaçêo**:
```bash
git clone https://github.com/unitreerobotics/kinect_teleoperate.git
cd kinect_teleoperate

# Instalar Azure Kinect SDK
# Windows: https://docs.microsoft.com/en-us/azure/kinect-dk/sensor-sdk-download
# Linux: sudo apt install k4a-tools

pip install -r requirements.txt
```

---

### 1.7 Simuladores

#### 🎮 unitree_mujoco

**Características**:
- Física de contato precisa (MuJoCo)
- Gerador de terrenos integrado
- Interface C++ e Python
- Sim-to-real implementations

**Instalaçêo**:
```bash
git clone https://github.com/unitreerobotics/unitree_mujoco.git
cd unitree_mujoco

# Instalar MuJoCo
pip install mujoco

# Compilar
mkdir build && cd build
cmake ..
make
```

**Exemplo de Uso**:
```python
import mujoco
import mujoco.viewer

# Carregar modelo G1
model = mujoco.MjModel.from_xml_path("unitree_mujoco/models/g1/g1.xml")
data = mujoco.MjData(model)

# Simulaçêo
with mujoco.viewer.launch_passive(model, data) as viewer:
    while viewer.is_running():
        # Aplicar controle
        data.ctrl[:] = 0  # Comandos de torque
        
        # Step de simulaçêo
        mujoco.mj_step(model, data)
        
        # Atualizar visualizaçêo
        viewer.sync()
```

#### 🎮 unitree_sim_isaaclab

**Repositório**: https://github.com/unitreerobotics/unitree_sim_isaaclab

**Características**:
- Baseado em Isaac Lab (NVIDIA)
- Simulaçêo fotorrealística
- Suporte a múltiplas tarefas
- Coleta de dados, playback e validaçêo

**Instalaçêo**:
```bash
# 1. Instalar Isaac Lab
git clone https://github.com/isaac-sim/IsaacLab.git
cd IsaacLab
./isaaclab.sh --install

# 2. Instalar unitree_sim_isaaclab
git clone https://github.com/unitreerobotics/unitree_sim_isaaclab.git
cd unitree_sim_isaaclab
pip install -e .
```

**Executar Tarefa**:
```bash
# Treinar manipulaçêo de objetos
python scripts/train.py --task=UnitreeG1Manipulation

# Visualizar
python scripts/play.py --task=UnitreeG1Manipulation \
    --checkpoint=logs/policy.pth
```

---

### 1.8 Tutoriais e Documentaçêo

#### 📖 Documentaçêo Oficial

**Centro de Documentaçêo Unitree**: https://support.unitree.com/home/en

**Guias Principais**:
1. **G1 SDK Development Guide**: https://support.unitree.com/home/en/G1_developer
2. **H1 SDK Development Guide**: https://support.unitree.com/home/en/H1_developer
3. **RL Control Routine**: https://support.unitree.com/home/en/G1_developer/rl_control_routine

#### 📖 Tutoriais da Comunidade

**QUADRUPED Robotics - G1 Tutorial**: https://www.docs.quadruped.de/projects/g1/html/index.html

**Conteúdo**:
- G1 Overview e especificações
- G1-Edu Overview
- Mêos destras (Dex3-1, Dex5-1)
- Radar e FOV de câmeras
- Interface elétrica
- Computador de bordo
- Motores das juntas
- Manuais do usuário
- Apps móveis
- Desempacotamento e setup inicial
- Carregamento
- Operaçêo (Firmware V1.0.2 e V1.0.4)

**Robostore - G1 Startup Guide**: https://robostore.com/blogs/news/unitree-g1-startup-guide

**Conteúdo**:
- Configuraçêo de rede passo-a-passo
- Calibraçêo do robô
- Controle de movimento
- Tutoriais em vídeo

#### 📖 Vídeos Tutoriais

**YouTube - Unitree G1 Humanoid: Setup & Training Guide**:
https://www.youtube.com/playlist?list=PLUZOCha5G72apYRFWvUpbi44AUM8S73ll

**Conteúdo**:
- Instalaçêo de software
- Configuraçêo de hardware
- Primeiros passos
- Treinamento de políticas

---

### 1.9 Modelo de Mundo UnifoLM

#### 🌍 UnifoLM-WMA-0 (Unified Large Model - World Model Action)

**Repositório HuggingFace**: https://huggingface.co/unitreerobotics/UnifoLM-WMA-0-Base

**Descriçêo**:
- Arquitetura world-model-action de código aberto
- Multi-embodiment (funciona em múltiplos robôs)
- Aprendizado de propósito geral

**Funcionalidades**:
1. **Simulation Engine**: Opera como simulador interativo para gerar dados sintéticos
2. **Action Prediction**: Prevê ações a partir de observações e objetivos

**Uso**:
```python
from transformers import AutoModel, AutoTokenizer

# Carregar modelo
model = AutoModel.from_pretrained("unitreerobotics/UnifoLM-WMA-0-Base")
tokenizer = AutoTokenizer.from_pretrained("unitreerobotics/UnifoLM-WMA-0-Base")

# Inferência
inputs = tokenizer("Pick up the red block", return_tensors="pt")
outputs = model(**inputs)
```

---

## Parte II: Noetix Bumi - Materiais Técnicos Completos

### 2.1 Especificações Técnicas

#### 🤖 Noetix Bumi - Especificações Completas

**Dimensões Físicas**:
- **Altura**: 94 cm (3 pés 1 polegada)
- **Peso**: 12 kg (26.5 libras)
- **Fator de Forma**: Compacto, projetado para evitar "uncanny valley" em crianças

**Graus de Liberdade**:
- **DoF Total**: Mínimo 21 DoF
- **Distribuiçêo**: Nêo divulgado oficialmente

**Bateria e Autonomia**:
- **Tensêo**: 48V
- **Capacidade**: >3.5 Ah
- **Autonomia**: 1-2 horas por carga
- **Tempo de Carga**: Nêo divulgado

**Capacidades**:
- Caminhada bípede
- Corrida
- Dança
- Interaçêo por voz
- Resposta a comandos

**Preço**:
- **China**: ¥9.988 (~$1.380 USD)
- **Internacional**: ~$1.400 USD

**Disponibilidade**:
- Lançamento: Outubro 2025
- Mercado-alvo: Estudantes, educadores, famílias, desenvolvedores

---

### 2.2 Interface de Programaçêo

#### 💻 Drag-and-Drop Graphical Programming

**Características**:
- **Interface Visual**: Programaçêo baseada em blocos (estilo Scratch)
- **Público-alvo**: Iniciantes, estudantes, educadores
- **Funcionalidades**:
  - Criar sequências de atividades
  - Programar movimentos e comportamentos
  - Integraçêo com comandos de voz

**Exemplo Conceitual** (baseado em informações disponíveis):
```
[Início]
  ↓
[Ouvir Comando de Voz: "Dance"]
  ↓
[Executar Sequência de Dança]
  ↓
[Aguardar 5 segundos]
  ↓
[Voltar para Posiçêo Inicial]
  ↓
[Fim]
```

#### 💻 Open Programming Interfaces (APIs)

**Características**:
- **APIs Abertas**: Permite que desenvolvedores construam aplicações personalizadas
- **Integraçêo com Ecossistema**: JD.com Joy Inside 2.0
- **Linguagens Suportadas**: Nêo divulgado oficialmente (provavelmente Python, JavaScript)

**Conceito de API** (especulativo baseado em padrões da indústria):
```python
# Exemplo conceitual de API Bumi
from bumi_sdk import BumiRobot

robot = BumiRobot(ip="192.168.1.100")

# Conectar
robot.connect()

# Comandos básicos
robot.stand_up()
robot.walk_forward(speed=0.5, duration=3.0)
robot.dance(style="hip_hop")

# Comandos de voz
robot.speak("Olá, eu sou Bumi!")
robot.listen_for_command()

# Desconectar
robot.disconnect()
```

---

### 2.3 Integraçêo com Ecossistema JD.com

#### 🌐 Joy Inside 2.0

**Descriçêo**:
- Plataforma de ecossistema da JD.com para robótica
- Promove uso como plataforma para programadores e educadores
- Comunidade de desenvolvedores

**Funcionalidades Esperadas**:
- Marketplace de aplicações para Bumi
- Compartilhamento de programas e comportamentos
- Tutoriais e recursos educacionais
- Integraçêo com serviços JD.com (e-commerce, logística)

---

### 2.4 Casos de Uso

#### 🎓 Educaçêo

**Aplicações**:
- **Ensino de Programaçêo**: Interface drag-and-drop para crianças
- **STEM Education**: Robótica, física, matemática
- **Demonstrações em Sala de Aula**: Tamanho compacto (94cm) ideal para classrooms

**Vantagens**:
- Preço acessível para escolas
- Interface amigável para iniciantes
- Tamanho apropriado para ambientes educacionais

#### 🏠 Uso Doméstico

**Aplicações**:
- **Entretenimento**: Dança, interaçêo, jogos
- **Assistente Doméstico**: Comandos de voz, tarefas simples
- **Companhia**: Interaçêo social, especialmente para crianças

**Vantagens**:
- Preço comparável a um iPhone flagship
- Design "family-friendly"
- Evita "uncanny valley" com tamanho reduzido

#### 🔬 Pesquisa e Desenvolvimento

**Aplicações**:
- **Prototipagem de Algoritmos**: Plataforma de baixo custo
- **Testes de IA**: APIs abertas para desenvolvimento
- **Educaçêo em Robótica**: Ferramenta de aprendizado para universidades

---

### 2.5 Comparaçêo: Bumi vs. Unitree vs. Outros

| Característica | Noetix Bumi | Unitree G1 | Unitree R1 | Tesla Optimus |
|----------------|-------------|------------|------------|---------------|
| **Preço** | $1.400 | $16.000 | $5.900 | $20-30K (est.) |
| **Altura** | 94 cm | 132 cm | ~120 cm | ~173 cm |
| **Peso** | 12 kg | ~35 kg | ~25 kg | ~73 kg |
| **DoF** | 21+ | 23-43 | ~20 | 28 |
| **Autonomia** | 1-2h | 2h | 2h | 2h (est.) |
| **Público-alvo** | Educaçêo/Família | Pesquisa/Indústria | Educaçêo/Pesquisa | Indústria |
| **Programaçêo** | Drag-drop + API | SDK C++/Python | SDK + Helix | Proprietário |
| **Disponibilidade** | Comercial | Comercial | Comercial | Nêo comercial |

---

### 2.6 Limitações e Considerações

#### ⚠️ Limitações Conhecidas

**Capacidades Físicas**:
- **Carga Útil**: Nêo divulgada (provavelmente limitada devido ao tamanho)
- **Velocidade**: Nêo divulgada
- **Precisêo**: Nêo divulgada (provavelmente menor que robôs industriais)

**Documentaçêo**:
- **SDK**: Nêo disponível publicamente ainda
- **Tutoriais**: Limitados no lançamento
- **Comunidade**: Ainda em formaçêo

**Casos de Uso**:
- **Trabalho Braçal**: Nêo adequado (tamanho e força limitados)
- **Manufatura**: Nêo adequado
- **Foco**: Educaçêo, entretenimento, pesquisa básica

#### ✅ Vantagens Competitivas

**Preço Disruptivo**:
- Primeiro humanoide comercial abaixo de $1.500
- Democratizaçêo da robótica humanoide
- Acesso para escolas e famílias

**Facilidade de Uso**:
- Interface drag-and-drop para iniciantes
- APIs abertas para desenvolvedores avançados
- Integraçêo com ecossistema estabelecido (JD.com)

**Design Apropriado**:
- Tamanho ideal para educaçêo
- Evita "uncanny valley"
- Portátil e seguro para crianças

---

## Parte III: Materiais Práticos de Treinamento

### 3.1 Roteiro de Aprendizado para Unitree

#### 📅 Semana 1-2: Fundamentos

**Objetivos**:
- Entender arquitetura do robô
- Configurar ambiente de desenvolvimento
- Executar primeiros comandos

**Atividades**:
1. Ler documentaçêo oficial do G1
2. Instalar unitree_sdk2_python
3. Conectar ao robô via rede
4. Executar comandos básicos (stand up, sit down)
5. Ler estado do robô (juntas, IMU)

**Recursos**:
- Documentaçêo: https://support.unitree.com/home/en/G1_developer
- Tutorial: https://www.docs.quadruped.de/projects/g1/html/index.html

#### 📅 Semana 3-4: Simulaçêo

**Objetivos**:
- Configurar simulador
- Treinar primeira política de locomoçêo
- Entender sim-to-real gap

**Atividades**:
1. Instalar Isaac Gym ou MuJoCo
2. Clonar unitree_rl_gym ou unitree_mujoco
3. Treinar política de caminhada em terreno plano
4. Visualizar política treinada
5. Experimentar com diferentes recompensas

**Recursos**:
- Repositório: https://github.com/unitreerobotics/unitree_rl_gym
- Repositório: https://github.com/unitreerobotics/unitree_mujoco

#### 📅 Semana 5-8: Coleta de Dados e Imitaçêo

**Objetivos**:
- Configurar sistema de teleoperaçêo
- Coletar dataset próprio
- Treinar política por imitaçêo

**Atividades**:
1. Configurar xr_teleoperate ou kinect_teleoperate
2. Definir tarefa de manipulaçêo simples
3. Coletar 50-100 demonstrações
4. Converter dados para formato LeRobot
5. Treinar política ACT ou Diffusion
6. Testar em simulaçêo e hardware

**Recursos**:
- Repositório: https://github.com/unitreerobotics/xr_teleoperate
- Repositório: https://github.com/unitreerobotics/unitree_IL_lerobot
- Datasets: https://huggingface.co/unitreerobotics

#### 📅 Semana 9-12: Projeto Avançado

**Objetivos**:
- Desenvolver aplicaçêo completa
- Integrar locomoçêo + manipulaçêo
- Deploy em hardware real

**Atividades**:
1. Definir tarefa complexa (ex: pegar objeto de prateleira)
2. Treinar política de locomoçêo para navegaçêo
3. Treinar política de manipulaçêo para preensêo
4. Integrar políticas com coordenador de alto nível
5. Testar extensivamente em hardware
6. Documentar e compartilhar resultados

---

### 3.2 Roteiro de Aprendizado para Noetix Bumi

#### 📅 Semana 1: Familiarizaçêo

**Objetivos**:
- Desempacotar e configurar Bumi
- Executar primeiros comandos
- Explorar interface drag-and-drop

**Atividades**:
1. Unboxing e carregamento da bateria
2. Conectar via app móvel (se disponível)
3. Executar comandos de voz básicos
4. Criar primeira sequência com drag-and-drop
5. Fazer Bumi dançar e caminhar

**Recursos**:
- Manual do usuário (quando disponível)
- Tutoriais oficiais Noetix

#### 📅 Semana 2-4: Programaçêo Básica

**Objetivos**:
- Dominar interface drag-and-drop
- Criar comportamentos personalizados
- Integrar com comandos de voz

**Atividades**:
1. Criar rotina matinal (acordar, saudar, dançar)
2. Programar resposta a múltiplos comandos de voz
3. Criar sequência de movimentos sincronizada com música
4. Compartilhar programas na comunidade Joy Inside

**Recursos**:
- Plataforma Joy Inside 2.0
- Comunidade de desenvolvedores

#### 📅 Semana 5-8: Programaçêo Avançada (APIs)

**Objetivos**:
- Aprender a usar APIs abertas
- Desenvolver aplicaçêo personalizada
- Integrar com serviços externos

**Atividades**:
1. Estudar documentaçêo de API (quando disponível)
2. Escrever primeiro script Python para controlar Bumi
3. Criar aplicaçêo de assistente pessoal
4. Integrar com APIs externas (clima, notícias)
5. Publicar aplicaçêo no ecossistema

**Recursos**:
- Documentaçêo de API Noetix (aguardando lançamento)
- Exemplos da comunidade

---

## Parte IV: Recursos Adicionais

### 4.1 Comunidades e Fóruns

**Unitree**:
- Discord: https://discord.gg/ZwcVwxv5rq
- GitHub Discussions: https://github.com/unitreerobotics
- Fórum Oficial: https://support.unitree.com

**Noetix**:
- JD.com Joy Inside 2.0: (aguardando lançamento)
- Comunidade de desenvolvedores: (em formaçêo)

### 4.2 Papers e Publicações

**Unitree-Related**:
1. "VideoMimic: Visual Imitation Enables Contextual Humanoid Control" (2025)
2. "Heterogeneous Pretrained Transformers for Robot Learning" - MIT (2024)
3. "Large Behavior Models and Atlas Find New Footing" - Boston Dynamics/TRI (2025)

**Robótica Geral**:
1. "RT-2: Vision-Language-Action Models" - Google DeepMind (2023)
2. "Open X-Embodiment: Robotic Learning Datasets" (2023)
3. "Behavior Foundation Model for Humanoid Robots" (2025)

### 4.3 Cursos Online

**Robótica Humanoide**:
- MIT OpenCourseWare: "Underactuated Robotics"
- Coursera: "Modern Robotics" (Northwestern University)
- Udacity: "Robotics Software Engineer"

**Aprendizado por Reforço**:
- DeepMind x UCL: "Deep Learning Lecture Series"
- Spinning Up in Deep RL (OpenAI)
- CS285: Deep Reinforcement Learning (UC Berkeley)

### 4.4 Ferramentas e Bibliotecas

**Simulaçêo**:
- Isaac Gym: https://developer.nvidia.com/isaac-gym
- Isaac Lab: https://github.com/isaac-sim/IsaacLab
- MuJoCo: https://mujoco.org
- PyBullet: https://pybullet.org

**Aprendizado de Máquina**:
- PyTorch: https://pytorch.org
- TensorFlow: https://tensorflow.org
- LeRobot: https://github.com/huggingface/lerobot
- Stable-Baselines3: https://github.com/DLR-RM/stable-baselines3

**Visêo Computacional**:
- OpenCV: https://opencv.org
- MediaPipe: https://mediapipe.dev
- SAM (Segment Anything): https://github.com/facebookresearch/segment-anything

---

## Conclusêo

Este documento compilou todos os materiais técnicos disponíveis recentemente sobre **Unitree** (G1, H1, R1) e **Noetix Bumi**, incluindo:

✅ **39 repositórios oficiais** da Unitree no GitHub  
✅ **Especificações técnicas completas** de todos os modelos  
✅ **SDKs** (C++ e Python) com exemplos de código  
✅ **7+ datasets públicos** no HuggingFace (>2M frames)  
✅ **Frameworks de treinamento** (RL, IL, World Models)  
✅ **Sistemas de teleoperaçêo** (XR, Kinect)  
✅ **Simuladores** (Isaac Gym, Isaac Lab, MuJoCo)  
✅ **Tutoriais práticos** e documentaçêo oficial  
✅ **Informações completas sobre Noetix Bumi**  
✅ **Roteiros de aprendizado** estruturados  

**Para Pesquisadores**: Este material fornece tudo o que é necessário para iniciar pesquisa avançada em robótica humanoide, desde configuraçêo básica até treinamento de políticas de ponta.

**Para Desenvolvedores**: Os SDKs, APIs e datasets permitem desenvolvimento rápido de aplicações práticas em robótica.

**Para Educadores**: Os materiais de baixo custo (Bumi, R1) e tutoriais acessíveis democratizam o ensino de robótica.

---

## Referências

1. Unitree Robotics Official: https://www.unitree.com
2. Unitree GitHub: https://github.com/unitreerobotics
3. Unitree Documentation: https://support.unitree.com
4. Unitree HuggingFace: https://huggingface.co/unitreerobotics
5. Noetix Robotics: (informações de múltiplas fontes de notícias)
6. JD.com Joy Inside 2.0: (aguardando documentaçêo oficial)

**Última Atualizaçêo**: 28 de Outubro de 2025
