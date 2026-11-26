# Repositórios Oficiais Unitree Robotics - Análise Técnica Completa

## Repositórios Principais (Atualizado: Outubro 2025)

### 1. unitree_rl_gym ⭐ 2.5k
**URL**: https://github.com/unitreerobotics/unitree_rl_gym
**Linguagem**: Python
**Descriçêo**: Implementaçêo de Reinforcement Learning baseada em Isaac Gym
**Robôs Suportados**: Go2, H1, H1_2, G1

**Uso Principal**:
- Treinamento de políticas de locomoçêo
- Simulaçêo massivamente paralela em GPU
- Exemplos de PPO para humanoides

### 2. unitree_rl_lab ⭐ 390 (NOVO - 2025)
**URL**: https://github.com/unitreerobotics/unitree_rl_lab
**Linguagem**: Python
**Descriçêo**: Implementaçêo RL baseada em IsaacLab (sucessor do Isaac Gym)
**Última Atualizaçêo**: 28 de Outubro de 2025

**Características**:
- Framework mais moderno que unitree_rl_gym
- Suporte a Isaac Sim completo
- Melhor integraçêo com NVIDIA Omniverse

### 3. xr_teleoperate ⭐ 1.1k
**URL**: https://github.com/unitreerobotics/xr_teleoperate
**Linguagem**: Python
**Descriçêo**: Teleoperaçêo usando dispositivos XR (Apple Vision Pro, PICO 4 Ultra)
**Robôs Suportados**: G1, H1_2

**Aplicações**:
- Coleta de dados de demonstraçêo
- Treinamento por imitaçêo
- Controle remoto imersivo

### 4. unitree_sdk2 ⭐ 688
**URL**: https://github.com/unitreerobotics/unitree_sdk2
**Linguagem**: C++
**Descriçêo**: SDK oficial versêo 2 para controle de robôs Unitree
**Robôs Suportados**: Go2, B2, H1, G1

**Características**:
- Baseado em CycloneDDS
- Interface de baixo nível para motores
- Serviços de alto nível (SLAM, navegaçêo)

### 5. unitree_sdk2_python ⭐ 442
**URL**: https://github.com/unitreerobotics/unitree_sdk2_python
**Linguagem**: Python
**Descriçêo**: Interface Python para unitree_sdk2

**Vantagens**:
- Prototipagem rápida
- Integraçêo com ML frameworks (PyTorch, TensorFlow)
- Mais fácil para iniciantes

### 6. unitree_mujoco ⭐ 629
**URL**: https://github.com/unitreerobotics/unitree_mujoco
**Linguagem**: C++
**Descriçêo**: Simulaçêo usando MuJoCo com implementações sim-to-real
**Características**:
- Gerador de terrenos integrado
- Interface C++ e Python
- Física de contato precisa

### 7. unitree_IL_lerobot ⭐ 446
**URL**: https://github.com/unitreerobotics/unitree_IL_lerobot
**Linguagem**: Python
**Descriçêo**: Framework de Imitation Learning usando LeRobot modificado
**Foco**: Mêos destras do G1

**Funcionalidades**:
- Coleta de dados de demonstraçêo
- Treinamento de políticas de manipulaçêo
- Testes em hardware real

### 8. unitree_sim_isaaclab ⭐ 223
**URL**: https://github.com/unitreerobotics/unitree_sim_isaaclab
**Linguagem**: Python
**Descriçêo**: Ambiente de simulaçêo baseado em Isaac Lab
**Última Atualizaçêo**: 9 de Outubro de 2025

**Capacidades**:
- Coleta de dados
- Playback de trajetórias
- Geraçêo de dados sintéticos
- Validaçêo de modelos

### 9. unitree_ros / unitree_ros2
**unitree_ros** ⭐ 1.1k (ROS1)
**unitree_ros2** ⭐ 436 (ROS2)
**Linguagem**: C++

**Conteúdo**:
- Arquivos URDF/Xacro de todos os robôs Unitree
- Controladores Gazebo
- Interfaces de comunicaçêo ROS
- Suporte para G1 (recém adicionado)

### 10. unifolm-world-model-action ⭐ 660 (NOVO)
**URL**: https://github.com/unitreerobotics/unifolm-world-model-action
**Linguagem**: Python
**Descriçêo**: Arquitetura world-model-action de código aberto da Unitree
**Versêo**: UnifoLM-WMA-0

**Inovaçêo**:
- Modelo de mundo multi-embodiment
- Aprendizado de propósito geral
- Arquitetura inspirada em LLMs

## Repositórios de Suporte

### kinect_teleoperate
**Descriçêo**: Teleoperaçêo do H1 usando Azure Kinect DK
**Aplicaçêo**: Alternativa de baixo custo ao XR

### point_lio_unilidar
**Descriçêo**: Adaptaçêo do Point-LIO para Unitree 4D LiDAR L1
**Funcionalidade**: SLAM usando apenas pointcloud e IMU integrado

### unitree_guide
**Descriçêo**: Algoritmos de controle do livro "Quadruped Robot Control Algorithm"
**Conteúdo**:
- Controle de motores
- Movimentos de pés
- Algoritmos de controle de força
- Suporte para simulaçêo e hardware real

### unitree_legged_sdk (Legacy)
**Descriçêo**: SDK para robôs antigos (Aliengo, A1, Go1, B1)
**Status**: Mantido para compatibilidade

## Modelos 3D

### unitree_model
**Descriçêo**: Modelos 3D de robôs para diferentes ambientes
**Formatos**: URDF, Xacro, MJCF, USD
**Robôs**: Todos os modelos Unitree

## Análise de Tendências (2025)

### Repositórios Mais Ativos (Últimas 4 Semanas)
1. **xr_teleoperate** - Atualizado 28/Out/2025
2. **unitree_rl_lab** - Atualizado 28/Out/2025
3. **unitree_mujoco** - Atualizado 24/Out/2025
4. **unitree_ros2** - Atualizado 17/Out/2025

### Foco de Desenvolvimento Atual
- **Teleoperaçêo XR**: Investimento pesado em coleta de dados
- **IsaacLab**: Migraçêo de Isaac Gym para Isaac Lab
- **Imitation Learning**: Framework LeRobot para manipulaçêo
- **World Models**: Arquitetura UnifoLM para aprendizado geral

### Estatísticas da Comunidade
- **Total de Seguidores**: 4.7k
- **Total de Repositórios**: 39
- **Repositórios Públicos Principais**: 10
- **Linguagens Principais**: C++, Python, C
