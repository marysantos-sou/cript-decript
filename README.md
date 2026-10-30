# cript-decript
Desafio de Cibersegurança: Simulação de Criptografia e Descriptografia com Python
> ⚠️ **Aviso Legal / Disclaimer**: Este projeto foi desenvolvido exclusivamente para fins educacionais e acadêmicos no contexto do Bootcamp de Cibersegurança da [DIO (Digital Innovation One)](https://www.dio.me/). Os scripts operam apenas sobre um arquivo de teste local específico e visam demonstrar conceitos de criptografia simétrica e conscientização sobre ameaças cibernéticas.
---
📌 Visão Geral do Projeto
Este repositório contém a implementação prática de uma simulação básica de criptografia e descriptografia de arquivos em ambiente local utilizando a linguagem Python e a biblioteca pyaes.
O objetivo é compreender na prática como funcionam os algoritmos criptográficos aplicados por softwares maliciosos (como ransomwares) e, a partir dessa compreensão, desenvolver estratégias defensivas de proteção, mitigação e resposta a incidentes.
---
📂 Estrutura do Repositório
```text
├── encrypter.py          # Script responsável por ler o arquivo, criptografar e renomear com nova extensão
├── decrypter.py          # Script responsável por reverter o processo utilizando a chave simétrica
├── teste.txt             # Arquivo de texto utilizado como amostra no teste local
└── README.md             # Documentação técnica do desafio
```
---
🧠 Conceitos Teóricos Abordados
1. Criptografia Simétrica (AES)
Utiliza a mesma chave tanto para o processo de cifragem (criptografia) quanto para a decifragem (descriptografia).
Algoritmo utilizado: AES (Advanced Encryption Standard), padrão mundial de criptografia por blocos.
2. Modo de Operação CTR (Counter Mode)
Transforma uma cifra de bloco em uma cifra de fluxo (stream cipher).
Gera o próximo fluxo de chaves criptografando valores sucessivos de um contador.
3. Chave de Criptografia
Nos scripts de exemplo, foi utilizada uma chave simétrica de 16 bytes (128 bits):
```python
  key = b"msantos2026santo"  # 16 caracteres / 128 bits
  ```
---
🚀 Como Executar o Projeto
Pré-requisitos
Python 3.8+ instalado.
Biblioteca `pyaes` instalada no ambiente Python.
1. Instalação das Dependências
No Windows:
```powershell
pip install pyaes
```
No Kali Linux / Debian / Ubuntu / WSL (Linux com PEP 668):
Em versões recentes do Kali Linux (2023+), Debian (12+) e Ubuntu (23.04+), o ambiente Python é protegido por padrão (externally managed environment). Você pode instalar utilizando um Ambiente Virtual (recomendado) ou via instalação direta com flag:
Opção A: Utilizando Ambiente Virtual (Recomendado)
```bash
# 1. Instale o pacote python3-venv (caso ainda não esteja instalado)
sudo apt update && sudo apt install -y python3-venv python3-full

# 2. Crie e ative o ambiente virtual
python3 -m venv .venv
source .venv/bin/activate

# 3. Instale a biblioteca
pip install pyaes
```
> 💡 *Dica:* Para desativar o ambiente virtual após o uso, basta digitar `deactivate`.
Opção B: Instalação Direta no Sistema / Kali Linux
```bash
pip install pyaes --break-system-packages
```
ou especificando o interpretador:
```bash
python3 -m pip install --break-system-packages pyaes
```
2. Executando a Criptografia
Certifique-se de que o arquivo de exemplo `teste.txt` existe no diretório e execute:
```bash
python encrypter.py
```
![encrypter](image/cript.png)

Resultado esperado:
O arquivo original `teste.txt` é removido.
É gerado o arquivo criptografado `teste.txt.ransomwaretroll`.
3. Executando a Descriptografia (Restauração)
Para restaurar o arquivo original a partir dos dados criptografados, execute:
```bash
python decrypter.py
```
![decrypter](image/decript.png)
Resultado esperado:
O arquivo criptografado `teste.txt.ransomwaretroll` é removido.
O arquivo original `teste.txt` é restaurado com seu conteúdo legível original.
---
🛡️ Medidas de Segurança e Prevenção Defensiva
O estudo do funcionamento desse tipo de ameaça reforça a necessidade de implementação de controles de segurança defensiva em ambientes corporativos e pessoais:
Estratégia de Backup (Regra 3-2-1):
Manter 3 cópias dos dados importantes;
Em 2 tipos de mídias diferentes;
Sendo 1 cópia armazenada offsite ou imutável (fora do alcance da rede local).
Princípio do Menor Privilégio (PoLP):
Usuários e processos devem possuir apenas os privilégios estritamente necessários para suas funções.
Soluções de EDR e Antivírus:
Monitoramento comportamental para detectar alterações massivas de arquivos e criação de extensões suspeitas.
Conscientização do Usuário:
Treinamento contínuo contra ataques de phishing e engenharia social (principais vetores de entrega de malwares).
---
🎓 Conclusão
A prática permitiu consolidar os fundamentos do uso de criptografia simétrica com Python, evidenciando tanto a eficiência dos algoritmos modernos de criptografia quanto a criticidade de políticas preventivas para proteção e integridade de dados.
