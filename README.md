## 🎒 Identificador de Objetos da Mochila Escolar

Projeto de acessibilidade que utiliza **Redes Neurais Convolucionais (RNC)** para identificar, em tempo real, objetos escolares dentro de uma mochila, fornecendo **feedback sonoro** ao usuário. A ideia é apoiar **pessoas com deficiência visual** no ambiente educacional.

---

## 📌 Objetivo

Criar uma prova de conceito utilizando **YOLOv5**, que:

* Detecta objetos escolares via webcam.
* Filtra apenas os itens relevantes.
* Fala os nomes dos objetos detectados, em português ou inglês.
* Pode futuramente identificar **objetos faltando**.

---

## 🧠 Tecnologias Utilizadas

| Componente                 | Ferramenta / Biblioteca                        |
| -------------------------- | ---------------------------------------------- |
| Rede Neural Convolucional  | YOLOv5 (pré-treinado - versão `yolov5s`)       |
| Processamento de imagem    | OpenCV                                         |
| Texto para fala (TTS)      | pyttsx3 (offline)                              |
| Framework de Deep Learning | PyTorch                                        |
| Interface                  | Tkinter                                        |
| Dataset                    | COCO (80 classes, incluindo objetos escolares) |

---

## 📸 Arquitetura Funcional

[Webcam] 
   ↓ 
[Redimensionamento e pré-processamento] 
   ↓ 
[YOLOv5 - Detecção de objetos] 
   ↓ 
[Filtro: apenas objetos escolares] 
   ↓ 
[Texto para fala com pyttsx3] 
   ↓ 
[Usuário ouve os objetos detectados]

---

## ✅ Pré-requisitos

Tenha o Python 3.12 instalado e, no terminal (PowerShell):
-> pip install torch torchvision opencv-python pyttsx3 yolov5

---

## 🗂️ Estrutura dos Arquivos

mochila_identificador/
├── main_gui.py     # Script da interface gráfica do usuário (graphic user interface)
├── main.py         # Script principal para detecção + feedback sonoro
├── README.md       # Este arquivo
├── teste_imagem.py # Script que utiliza imagens para detecção de objetos

---

## 🚀 Como Executar

1. Clone ou copie os arquivos para um diretório local:
2. No terminal, acesse a pasta do projeto:

cd <caminho do seu repositorio que contém o projeto>
python <nome do seu arquivo>


3. Aguarde o carregamento do modelo.
4. Mantenha a webcam apontada para os objetos escolares.
5. Pressione **`q`** para sair.

---

## 🖼️ Interface Gráfica com Tkinter

Além da versão por terminal, o projeto inclui uma **interface gráfica amigável**, construída com **Tkinter**, para facilitar o uso por qualquer pessoa — especialmente em situações onde a linha de comando não é ideal.

### Recursos da interface:

* ✅ **Botão “Iniciar Detecção”**: ativa a webcam e começa o processo de identificação.
* 🛑 **Botão “Sair”**: encerra a execução com segurança.
* 🌐 **Botão “Alternar Idioma” (PT/EN)**: muda entre os idiomas **Português** e **Inglês** para o feedback sonoro.
* 📦 **Lista de Objetos Esperados**: mostra os itens que deveriam estar na mochila.
* 🚨 **Aviso de Faltando**: se algum item da lista não for detectado, o sistema avisa por voz, por exemplo:

  * **Português**: “Faltando mochila”
  * **Inglês**: “backpack is missing”

### Como usar:

* Execute o script `main_gui.py`:
-> python main_gui.py
 
* Use os botões para iniciar, mudar idioma e encerrar o sistema.
* A detecção é mostrada visualmente com *bounding boxes* na janela da câmera e informada por áudio.

---

Perfeito, Giulia! Aqui está o trecho pronto para adicionar ao seu `README.md` com a nova seção **“Teste com Imagens Estáticas”**:

---

## 🖼️ Teste com Imagens Estáticas

Além da detecção ao vivo com webcam, você pode testar o modelo com **imagens salvas no computador**, útil para:

* Fazer testes mais rápidos.
* Avaliar o desempenho em cenários específicos.
* Gerar capturas de tela para relatórios ou apresentações.

### ✅ Como usar

1. **Coloque uma imagem** (ex: `mochila.jpg`) na mesma pasta do projeto.
2. Execute com:
-> python teste_imagem.py (ou seja qual for o nome do seu arquivo que contenha o código que utiliza imagens estáticas).

---

### 📌 Observação

Certifique-se de que a imagem contém objetos compatíveis com o **dataset COCO** (`book`, `backpack`, `scissors`). Outros objetos podem ser ignorados ou mal classificados.

---

## 🧾 Objetos Detectáveis

O modelo detecta os seguintes objetos escolares (do dataset COCO):

* `"backpack"` (mochila)
* `"book"` (livro)
* `"scissors"` (tesoura)
* (Outros podem ser simulados, como `"pen"` usando `"cell phone"`)

---

## 🔊 Acessibilidade

O feedback é feito por voz com a biblioteca **`pyttsx3`**, que funciona offline e lê os nomes dos objetos detectados em tempo real.

---

## 🛠️ Melhorias Futuras

* Identificar objetos faltando com base em uma lista de materiais esperados.
* Suporte a múltiplos idiomas.
* Treinamento personalizado com fotos reais de materiais escolares já que o dataset COCO não possui todas as classes que represnetam materiais escolares.

---

## 🧑‍🏫 Exemplos de objetos escolares presentes no dataset COCO

| Objeto Real       | Classe COCO Correspondente  |
| ----------------- | --------------------------- |
| Mochila           | `backpack` (38)             |
| Livro             | `book` (65)                 |
| Tesoura           | `scissors` (68)             |
| Relógio de parede | `clock` (66)                |
| Copo              | `cup` (45)                  |
| Notebook (laptop) | `laptop` (21)               |
| Celular           | `cell phone` (25)           |


## ✅ Lista completa das 80 classes do COCO 

0:  person           20: tv               40: skateboard         60: toothbrush
1:  bicycle          21: laptop           41: surfboard          61: hair drier
2:  car              22: mouse            42: tennis racket      62: toaster
3:  motorcycle       23: remote           43: bottle             63: sink
4:  airplane         24: keyboard         44: wine glass         64: refrigerator
5:  bus              25: cell phone       45: cup                65: book
6:  train            26: microwave        46: fork               66: clock
7:  truck            27: oven             47: knife              67: vase
8:  boat             28: toaster          48: spoon              68: scissors
9:  traffic light    29: sink             49: bowl               69: teddy bear
10: fire hydrant     30: refrigerator     50: banana             70: hair brush
11: stop sign        31: book             51: apple              71: toothbrush
12: parking meter    32: clock            52: sandwich           72: hair drier
13: bench            33: vase             53: orange             73: tv
14: bird             34: scissors         54: broccoli           74: laptop
15: cat              35: teddy bear       55: carrot             75: mouse
16: dog              36: hair drier       56: hot dog            76: remote
17: horse            37: toothbrush       57: pizza              77: keyboard
18: sheep            38: backpack         58: donut              78: cell phone
19: cow              39: umbrella         59: cake               79: microwave

---

## 👩‍💻 Desenvolvedora

**Giulia e João**
Projeto de Redes Neurais Artificiais (RNA)
Curso de Ciência da Computação – IESB
