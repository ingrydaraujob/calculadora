# calculadora
 Minha primeira calculadora em python 

# Documentação do Código da Calculadora com Tkinter
Este projeto cria uma calculadora simples usando a biblioteca Tkinter do Python. A interface tem uma tela onde o usuário pode digitar números e operadores, além de botões que permitem fazer operações matemáticas básicas, como soma, subtração, multiplicação, divisão e porcentagens. A calculadora também tem a opção de limpar a tela e calcular o resultado das expressões inseridas.

# Estrutura do Código

## Importação de Bibliotecas
O programa usa a biblioteca Tkinter para criar a interface gráfica e algumas de suas classes auxiliares:
```bash
from tkinter import *
from tkinter import ttk
```
## Paleta de Cores
As cores são definidas para padronizar a aparência da interface:
```bash
cor1 = "#030303" #cor escolhida preta
cor2 = "#faf7f7" #cor escolhida branco 
cor3 = "#38576b" #cor escolhida azul
cor4 = "#ECEFF1" #cor escolhida cinza
cor5 = "#f08b1f" #cor escolhida amarelo  
```

## Configuração da Janela Principal
A janela principal é criada com Tk() e configurada com um título, tamanho fixo e cor de fundo:
```bash
janela = Tk()
janela.title("Calculadora")
janela.geometry("235x310")
janela.config(bg=cor1)
```
## Criação de Frames
A interface é dividida em dois frames:
1.Frame Tela: Exibe os valores digitados e o resultado.
2.Frame Corpo: Contém os botões da calculadora.
```bash 
frame_tela = Frame(janela, width=235, height=50, bg=cor3)
frame_tela.grid(row=0, column=0)

frame_corpo = Frame(janela, width=235, height=268)
frame_corpo.grid(row=1, column=0)
```

## Variáveis Globais
1.todos_valores: Armazena os números e operadores digitados.
2.valor_texto: Atualiza o texto exibido na tela da calculadora.
```bash
todos_valores = ""
valor_texto = StringVar()
```

## Funções
Adicionar Valores
A função entrar_valor atualiza todos_valores e exibe o conteúdo na tela.
```bash
def entrar_valor(event):
    global todos_valores
    todos_valores = todos_valores + str(event)
    valor_texto.set(todos_valores)
```
## Calcular Resultado
A função calcular avalia a expressão digitada usando eval() e exibe o resultado.
```bash
def calcular():
    global todos_valores
    resultado = eval(todos_valores)
    valor_texto.set(str(resultado))
```
## Limpar Tela
A função limpar_tela redefine todos_valores e limpa a tela.
```bash
def limpar_tela():
    global todos_valores
    todos_valores = ""
    valor_texto.set("")
```
## Criação do Display
A tela é criada com um Label configurado para exibir o conteúdo centralizado:
```bash
app_label = Label(frame_tela, textvariable=valor_texto, width=16, height=2, padx=7, relief=FLAT, anchor="e", justify=RIGHT, font=("ivy 18"), bg=cor3, fg=cor2)
app_label.place(x=0, y=0)
```
## Criação dos Botões
Os botões são configurados para chamar as funções apropriadas ao serem clicados. A disposição segue uma grade organizada com espaçamento adequado:
```bash
Criação dos Botões

Os botões são configurados para chamar as funções apropriadas ao serem clicados. A disposição segue uma grade organizada com espaçamento adequado:

b_1 = Button(frame_corpo, command=limpar_tela, text="C", width=11, height=2, bg=cor4, font=("ivy 13 bold"), relief=RAISED, overrelief=RIDGE)
b_1.place(x=0, y=0)

b_2 = Button(frame_corpo, command=lambda: entrar_valor("%"), text="%", width=5, height=2, bg=cor4, font=("ivy 13 bold"), relief=RAISED, overrelief=RIDGE)
b_2.place(x=118, y=0)

b_3 = Button(frame_corpo, command=lambda: entrar_valor("/"), text="/", width=5, height=2, bg=cor5, fg=cor2, font=("ivy 13 bold"), relief=RAISED, overrelief=RIDGE)
b_3.place(x=177, y=0)


```
## Inicialização
O programa entra em um loop para manter a janela aberta e interativa:
```bash
janela.mainloop()
```
