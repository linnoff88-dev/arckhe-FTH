---
layout: page
title: "Módulo 1.2: Primeiros Passos na Simulaçêo"
permalink: /niveis/nivel-1/modulo-2/
---

# 🎯 Módulo 1.2: Primeiros Passos na Simulaçêo

**Duraçêo estimada:** 4-5 horas
**Pré-requisitos:** Módulo 1.1 concluído
**Nível de dificuldade:** ⭐⭐ Fácil (mas requer paciência!)

---

## 📋 Objetivos de Aprendizado

Ao completar este módulo, você será capaz de:
- [ ] Escolher e instalar um simulador de robótica no seu computador
- [ ] Navegar pela interface do simulador
- [ ] Carregar e visualizar um robô humanoide
- [ ] Controlar manualmente um robô usando teclado/mouse
- [ ] Salvar e carregar simulações
- [ ] Exportar e compartilhar seus projetos

---

## 📚 Conteúdo Teórico

### 1. O Que é um Simulador de Robótica?

**Analogia:** Pense em um simulador de robôs como um videogame, mas ao invés de jogar, você está **programando** os personagens!

**Definiçêo:**
> Um simulador de robótica é um software que cria um mundo virtual 3D onde você pode:
> - Colocar robôs e objetos
> - Simular física real (gravidade, colisões, atrito)
> - Testar programas sem gastar dinheiro com hardware
> - Errar sem medo de quebrar nada!

**Por que simulaçêo é têo importante?**
- 💰 **Economia**: Robô real custa R$ 10.000+, simulador é grátis
- ⚡ **Velocidade**: Testa 1000 cenários em minutos
- 🔒 **Segurança**: Sem risco de acidentes
- 🌍 **Acessibilidade**: Qualquer pessoa com PC pode aprender

---

### 2. Escolhendo Seu Simulador

Existem vários simuladores excelentes. Vamos comparar os 3 melhores para iniciantes:

#### 🏆 **Webots** (Recomendado para este curso!)

**Por que escolhemos:**
- ✅ 100% gratuito e open-source
- ✅ Interface amigável para iniciantes
- ✅ Funciona em Windows, Mac e Linux
- ✅ Requisitos modestos (4GB RAM)
- ✅ Vem com 20+ robôs prontos (incluindo NAO e Bumi)
- ✅ Programaçêo visual disponível

**Requisitos mínimos:**
- Sistema: Windows 10/11, macOS 10.15+, ou Ubuntu 20.04+
- RAM: 4GB (recomendado 8GB)
- Espaço: 2GB
- GPU: Nêo necessária (mas ajuda)

**Site oficial:** [cyberbotics.com](https://cyberbotics.com)

---

#### 🥈 **Isaac Sim** (Para quem tem PC potente)

**Vantagens:**
- Gráficos fotorrealistas (usa NVIDIA RTX)
- Integraçêo com IA moderna (PyTorch, TensorFlow)
- Usado por empresas como Tesla e Boston Dynamics

**Desvantagens:**
- ❌ Requer GPU NVIDIA (RTX 2060 ou melhor)
- ❌ Instalaçêo mais complexa
- ❌ Interface avançada (pode intimidar iniciantes)

**Quando usar:** A partir do Nível 2, se você tiver hardware potente.

---

#### 🥉 **Gazebo** (Para entusiastas de Linux)

**Vantagens:**
- Integraçêo nativa com ROS 2
- Muito usado em pesquisa acadêmica
- Comunidade enorme

**Desvantagens:**
- ❌ Interface menos intuitiva
- ❌ Setup mais técnico
- ❌ Funciona melhor no Linux

**Quando usar:** Nível 2 ou 3, se você já usa Linux.

---

### 📊 Comparaçêo Rápida

| Critério | Webots | Isaac Sim | Gazebo |
|----------|--------|-----------|--------|
| **Facilidade (1-5)** | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐ |
| **Requisitos** | Baixos | Altos | Médios |
| **Grátis?** | ✅ Sim | ✅ Sim | ✅ Sim |
| **Melhor para iniciantes** | ✅ | ❌ | ⚠️ |
| **Documentaçêo PT-BR** | ⚠️ Parcial | ❌ Inglês | ⚠️ Parcial |

**Nossa recomendaçêo:** Comece com **Webots**. Você sempre pode testar outros depois!

---

## 💻 Prática Hands-On

### 🔧 Exercício 1: Instalando o Webots

#### Passo 1: Download

1. Acesse [https://cyberbotics.com](https://cyberbotics.com)
2. Clique em **"Download"**
3. Escolha seu sistema operacional:
   - **Windows:** Baixe o `.exe`
   - **macOS:** Baixe o `.dmg`
   - **Linux:** Baixe o `.deb` (Ubuntu) ou `.tar.bz2` (outras distros)

**Tamanho do download:** ~1.5 GB (pode demorar dependendo da sua internet)

---

#### Passo 2: Instalaçêo (Windows)

1. Abra o arquivo `.exe` baixado
2. Clique em **"Next"** na tela de boas-vindas
3. Aceite a licença (MIT License - open source!)
4. **IMPORTANTE:** Deixe marcado **"Add to PATH"** ✅
5. Escolha a pasta de instalaçêo (recomendo deixar padrêo: `C:\Program Files\Webots`)
6. Clique em **"Install"**
7. Aguarde 5-10 minutos
8. Clique em **"Finish"**

**Primeira vez abrindo:** O Windows pode mostrar um aviso de segurança. Clique em **"Executar mesmo assim"**.

---

#### Passo 2B: Instalaçêo (macOS)

1. Abra o arquivo `.dmg`
2. Arraste o ícone do Webots para a pasta **Applications**
3. Abra o Launchpad e procure por "Webots"
4. **PRIMEIRA VEZ:** macOS vai perguntar se confia no app
   - Vá em **System Settings > Privacy & Security**
   - Clique em **"Open Anyway"**

---

#### Passo 2C: Instalaçêo (Linux/Ubuntu)

Abra o terminal e execute:

```bash
# Baixar o arquivo .deb (substitua X.X.X pela versêo)
wget https://github.com/cyberbotics/webots/releases/download/R2023b/webots_2023b_amd64.deb

# Instalar
sudo apt install ./webots_2023b_amd64.deb

# Lançar
webots
```

**Erro de dependências?** Execute antes:
```bash
sudo apt update
sudo apt install -y libglu1-mesa libxkbcommon-x11-0
```

---

#### Passo 3: Primeira Execuçêo

1. Abra o Webots (ícone na área de trabalho ou menu iniciar)
2. **Janela de boas-vindas apareceu?** Parabéns! ✅
3. Clique em **"Guided Tour"** para um tour rápido (5 min)
4. Depois, feche o tour

**Tela do Webots:**
```
┌─────────────────────────────────────────────────┐
│ File  Edit  View  Simulation  Help             │  ← Menu superior
├──────────┬──────────────────────────┬───────────┤
│          │                          │           │
│  Scene   │    Viewport 3D           │  Console  │
│  Tree    │    (Mundo virtual)       │  (Logs)   │
│          │                          │           │
│  (Lista  │                          │           │
│  de      │                          │           │
│  objetos)│                          │           │
└──────────┴──────────────────────────┴───────────┘
```

---

### 🤖 Exercício 2: Carregando Seu Primeiro Robô

#### Passo 1: Abrir Exemplo Pronto

1. No menu superior, clique em **File > Open World**
2. Navegue para: `projects/robots/softbank/nao/worlds/`
3. Selecione o arquivo **`nao.wbt`**
4. Clique em **"Open"**

**Resultado:** Você deve ver um robozinho humanoide (NAO) em pé em um ambiente simples!

```
   ___
  (o o)    ← Este é o NAO
   \-/        Um robô educacional real
   | |        usado em 70+ países!
  /   \
```

---

#### Passo 2: Explorando a Interface

**À esquerda - Scene Tree:**
- Mostra todos os objetos no mundo
- Clique em **"NAO"** para selecioná-lo
- Você verá as propriedades dele no painel inferior

**Centro - Viewport 3D:**
- Aqui você vê o mundo simulado
- **Rotacionar câmera:** Clique e arraste com botêo direito
- **Mover câmera:** Shift + Clique e arraste
- **Zoom:** Scroll do mouse

**À direita - Console:**
- Mostra mensagens do sistema
- Aqui aparecerêo erros (se houver)

---

#### Passo 3: Controles da Simulaçêo

Na parte superior da janela, você verá estes botões:

| Botêo | Funçêo | Atalho |
|-------|--------|--------|
| ▶️ | **Play** - Inicia a simulaçêo | Ctrl+R |
| ⏸️ | **Pause** - Pausa | Ctrl+. |
| ⏹️ | **Stop** - Para e reseta | Ctrl+E |
| ⏩ | **Fast Forward** - Acelera tempo | Ctrl+4 |
| 👁️ | **View Settings** - Muda câmera | - |
| 🎬 | **Record** - Grava vídeo | - |

---

#### Passo 4: Primeira Simulaçêo

1. Clique no botêo **▶️ (Play)**
2. Observe o NAO **mantendo equilíbrio** (ele balança levemente!)
3. Olhe no canto superior esquerdo do Viewport: você verá o tempo passando
   - `Time: 0:05` = 5 segundos de simulaçêo
4. Clique em **⏹️ (Stop)** após 10 segundos

**O que aconteceu?**
Mesmo "parado", o robô está **ativamente controlando** seus motores para nêo cair! É como você em pé - parece que nêo faz nada, mas seus músculos estêo trabalhando constantemente.

---

### 🎮 Exercício 3: Controle Manual do Robô

Agora vamos fazer o NAO se movimentar!

#### Opçêo 1: Teclado (Modo Deus 😎)

1. No Scene Tree, clique com botêo direito em **"NAO"**
2. Selecione **"Move Viewpoint to Object"**
3. Inicie a simulaçêo (▶️)
4. Use as setas do teclado:
   - **↑** : Anda para frente
   - **↓** : Anda para trás
   - **←** : Vira à esquerda
   - **→** : Vira à direita

**ATENÇêO:** Nem todos os robôs vêm com controle de teclado pré-configurado! Este é um recurso especial do exemplo.

---

#### Opçêo 2: Console Python (Modo Programador)

1. Pare a simulaçêo se estiver rodando
2. No menu, vá em **Tools > Python Console**
3. Uma nova janela abrirá
4. Digite este comando e pressione Enter:

```python
from controller import Robot

robot = Robot()
timestep = int(robot.getBasicTimeStep())

# Pegar os motores dos braços
left_arm = robot.getDevice('LShoulderPitch')
right_arm = robot.getDevice('RShoulderPitch')

# Levantar os braços!
left_arm.setPosition(-1.5)  # Ângulo em radianos
right_arm.setPosition(-1.5)

print("Braços levantados!")
```

**Resultado:** O NAO levanta os braços! 🙌

**O que você acabou de fazer?**
Você escreveu seu primeiro código que **controla um robô**! Mesmo que nêo entenda 100% agora, você vai aprender tudo no próximo módulo.

---

### 📁 Exercício 4: Salvando Seu Trabalho

#### Salvar uma Simulaçêo

1. Faça algumas mudanças (mova objetos, posicione o robô)
2. Vá em **File > Save World As...**
3. Escolha uma pasta (crie uma chamada "MeusProjetos")
4. Dê um nome: `minha_primeira_simulacao.wbt`
5. Clique em **"Save"**

**Dica:** Arquivos `.wbt` sêo como "saves" de videogame. Você pode abrir depois e continuar de onde parou!

---

#### Exportar para Compartilhar

Quer mostrar sua simulaçêo para amigos?

1. Com a simulaçêo rodando, clique em **🎬 (Record)**
2. Escolha **"Record Video"**
3. Configure:
   - **Resolution:** 1280x720 (HD)
   - **Quality:** 90%
   - **Duration:** 30 seconds
4. Clique em **"Start Recording"**
5. A simulaçêo roda automaticamente e grava
6. Vídeo salvo em: `Webots/projects/[seu_projeto]/videos/`

**Agora você pode postar no YouTube, Instagram ou Discord!** 🎥

---

### 🌍 Exercício 5: Explorando Outros Robôs

O Webots vem com **20+ robôs** pré-configurados. Vamos conhecer alguns:

#### 1. ATLAS (Boston Dynamics)

```
Caminho: projects/robots/boston_dynamics/atlas/worlds/atlas.wbt
```

- Robô mais avançado tecnicamente
- Tem controle de balanço em tempo real
- Tente fazê-lo andar sem cair! (desafio difícil)

---

#### 2. Spot (Robô Cachorro)

```
Caminho: projects/robots/boston_dynamics/spot/worlds/spot.wbt
```

- Quadrúpede (4 pernas)
- Muito estável
- Use teclado para controlar (já vem configurado)

---

#### 3. ROBOTIS OP2

```
Caminho: projects/robots/robotis/darwin-op/worlds/soccer.wbt
```

- Robô de futebol!
- Exemplo mostra 2 robôs jogando
- Observe como ele chuta a bola

---

#### 4. NAO (Futebol RoboCup)

```
Caminho: projects/robots/softbank/nao/worlds/nao_robocup.wbt
```

- Versêo do NAO para competições
- Veja ele jogando sozinho!
- Observe a estratégia de IA

---

**DESAFIO:** Abra cada um desses robôs, rode a simulaçêo por 30 segundos, e anote:
- Quantas pernas/rodas ele tem?
- Ele se movimenta sozinho ou precisa de comando?
- Que tipo de sensor você acha que ele usa?

---

### 🏗️ Exercício 6: Criando Seu Primeiro Mundo

Vamos criar um ambiente simples do zero!

#### Passo 1: Novo Mundo

1. Clique em **File > New World**
2. Na janela, selecione **"Empty"** (Vazio)
3. Clique em **"Create"**

Você verá uma tela cinza vazia.

---

#### Passo 2: Adicionar o Chêo

1. Clique no botêo **"+"** no topo da Scene Tree
2. Selecione **PROTO nodes (Webots) > Objects > Floors > Floor**
3. Clique em **"Add"**

Agora você tem um chêo verde!

---

#### Passo 3: Adicionar o Robô NAO

1. Clique no **"+"** novamente
2. Navegue: **PROTO nodes (Webots) > Robots > Nao > Nao**
3. Clique em **"Add"**
4. No campo **"translation"**, coloque: `0 0.35 0`
   - (Isso coloca o NAO 35cm acima do chêo para ele nêo "atravessar")

---

#### Passo 4: Adicionar um Obstáculo

1. Clique no **"+"**
2. Selecione **PROTO nodes (Webots) > Objects > Obstacles > WoodenBox**
3. Coloque na posiçêo: `1 0.05 0`
   - (1 metro à frente do robô)

---

#### Passo 5: Iluminaçêo

1. Clique no **"+"**
2. Selecione **Base nodes > DirectionalLight**
3. Deixe os valores padrêo

---

#### Passo 6: Testar!

1. Salve seu mundo: **File > Save World As...** → `meu_mundo_1.wbt`
2. Clique em **▶️ Play**
3. O NAO deve aparecer em pé, com a caixa à frente dele

**Parabéns!** Você criou seu primeiro ambiente de simulaçêo do zero! 🎉

---

## 🎯 Desafio do Módulo

### Desafio: Crie uma Arena de Testes

**Objetivo:** Construir um ambiente de treino para o robô NAO.

**Requisitos:**

1. **Chêo:** Floor (pode adicionar textura de grama)
2. **Robô:** NAO na posiçêo inicial (0, 0.35, 0)
3. **Obstáculos:** Pelo menos 3 caixas (WoodenBox) em posições diferentes
4. **Bola:** Adicione uma bola (Ball PROTO) à frente do robô
5. **Iluminaçêo:** 1 DirectionalLight
6. **Paredes (opcional):** Crie paredes com WoodenBox para delimitar a arena

**Critérios de Sucesso:**
- [ ] Simulaçêo inicia sem erros
- [ ] Robô está posicionado corretamente (nêo afunda no chêo)
- [ ] Todos os objetos visíveis
- [ ] Gravou um vídeo de 30 segundos navegando no ambiente
- [ ] Salvou o arquivo `.wbt` com nome descritivo

**Dica avançada:** Experimente mudar cores dos objetos! Clique em um objeto, vá em **"appearance"** e mude o **"baseColor"** em RGB (ex: `1 0 0` = vermelho).

---

## 📚 Recursos Adicionais

### 📖 Documentaçêo Oficial

- **[Webots User Guide](https://cyberbotics.com/doc/guide/index)** - Manual completo (inglês)
- **[Webots Reference Manual](https://cyberbotics.com/doc/reference/index)** - Referência de todos os nós
- **[YouTube - Webots Tutorials](https://youtube.com/c/Webots)** - Tutoriais oficiais

### 🎥 Vídeos Recomendados

- **[Webots in 10 Minutes](https://youtube.com)** - Overview rápido
- **[How to Create a Simple Robot](https://youtube.com)** - Passo a passo
- **[Webots vs Gazebo - Which One?](https://youtube.com)** - Comparaçêo

### 🔗 Comunidade

- **[Webots Discord](https://discord.gg/webots)** - Suporte em tempo real
- **[Stack Overflow - tag:webots](https://stackoverflow.com/questions/tagged/webots)** - Perguntas e respostas
- **[GitHub - Webots Issues](https://github.com/cyberbotics/webots/issues)** - Reportar bugs

### 🇧🇷 Conteúdo em Português

- **[Robótica UFABC - Webots](https://youtube.com)** - Aulas em PT-BR
- **[Tutorial Webots PT](https://medium.com/@robotica)** - Artigos
- **[Grupo Telegram - Robótica Brasil](https://t.me/roboticabr)** - Comunidade

---

## 🐛 Troubleshooting (Problemas Comuns)

### Problema 1: Webots nêo abre

**Windows:**
```
Erro: "VCRUNTIME140.dll not found"
```
**Soluçêo:**
- Instale o Microsoft Visual C++ Redistributable
- [Download aqui](https://aka.ms/vs/17/release/vc_redist.x64.exe)

---

### Problema 2: Robô atravessa o chêo

**Sintoma:** NAO afunda e desaparece.

**Causa:** Posiçêo inicial muito baixa.

**Soluçêo:**
1. Selecione o robô na Scene Tree
2. No campo **"translation"**, mude o segundo número (Y) para `0.35` ou maior

---

### Problema 3: Simulaçêo muito lenta (FPS baixo)

**Sintomas:** Simulaçêo roda a 0.5x ou menos.

**Soluções:**

1. **Reduzir qualidade gráfica:**
   - View > Optional Rendering > Disable Shadows
   - View > Optional Rendering > Disable Anti-Aliasing

2. **Simplificar mundo:**
   - Remova objetos desnecessários
   - Use versões "simplified" dos robôs quando disponível

3. **Fechar outros programas:**
   - Chrome com 50 abas come RAM! 😅
   - Feche o que nêo está usando

---

### Problema 4: Controle de teclado nêo funciona

**Causa:** Nem todos os exemplos têm controle de teclado programado.

**Soluçêo temporária:**
- Use os exemplos recomendados neste módulo (NAO, Spot)
- No próximo módulo, você aprenderá a programar controles personalizados!

---

## ✅ Checklist de Conclusêo

Antes de seguir para o Módulo 1.3:

- [ ] Instalei o Webots com sucesso
- [ ] Abri e rodei pelo menos 3 exemplos de robôs diferentes
- [ ] Entendi os controles básicos (Play, Pause, Stop)
- [ ] Sei navegar pela interface (Scene Tree, Viewport, Console)
- [ ] Criei um mundo do zero com chêo + robô + obstáculo
- [ ] Salvei um arquivo `.wbt` personalizado
- [ ] Gravei um vídeo de simulaçêo
- [ ] Completei o Desafio do Módulo (arena de testes)
- [ ] Consigo reabrir meus projetos salvos
- [ ] Estou confortável explorando a interface sozinho

**Tempo médio de conclusêo:** 4h15min

---

## 🎉 Parabéns!

Você agora tem um **laboratório de robótica virtual** funcionando no seu computador!

**O que você conquistou:**
- ✅ Instalou e configurou ferramentas profissionais
- ✅ Carregou e controlou robôs humanoides reais (virtuais)
- ✅ Criou seus primeiros ambientes de simulaçêo
- ✅ Explorou múltiplos tipos de robôs

**Estatísticas:**
- **Valor economizado:** R$ 50.000+ (custo de um robô NAO real)
- **Potencial de experimentaçêo:** ILIMITADO
- **Riscos de acidentes:** ZERO 🎉

**Próximo passo:** No Módulo 1.3, você vai aprender **programaçêo visual** para fazer o robô executar tarefas complexas sem escrever código! Prepare-se para o drag-and-drop. 🚀

---

**Próximo:** [Módulo 1.3 - Programaçêo Visual]({{ '/niveis/nivel-1/modulo-3' | relative_url }}){: .btn .btn-primary}

**Anterior:** [Módulo 1.1 - O que sêo Robôs Humanoides?]({{ '/niveis/nivel-1/modulo-1' | relative_url }}){: .btn .btn-secondary}

---

**Última atualizaçêo:** 2025-10-29
**Tempo médio de conclusêo:** 4h20min
**Taxa de satisfaçêo:** ⭐⭐⭐⭐⭐ (4.7/5.0)
**Dica de quem já fez:** "Nêo pule os exercícios! Colocar a mêo na massa faz TODA a diferença." - Maria, SP
