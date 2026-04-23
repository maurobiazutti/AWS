# Guia de Permissões no Linux (chmod & chown)

No Linux, tudo é arquivo. Para garantir a segurança, cada arquivo ou diretório possui regras estritas sobre quem pode ler, alterar ou executar.

---

## 1. A Estrutura das Permissões
As permissões são divididas em três grupos de usuários:

1.  **Owner (u):** O proprietário (quem criou o arquivo).
2.  **Group (g):** Usuários que pertencem ao grupo do arquivo.
3.  **Others (o):** Qualquer outro usuário no sistema.

Ao dar um `ls -l`, você verá algo como `-rwxr-xr--`. 
* O primeiro caractere indica o tipo (`-` para arquivo, `d` para diretório).
* Os 9 caracteres seguintes são as permissões (3 para cada grupo).

---

## 2. Tipos de Permissão

| Letra | Significado | Valor Binário | Ação em Arquivos | Ação em Diretórios |
| :--- | :--- | :--- | :--- | :--- |
| **r** | Read (Leitura) | **4** | Ler o conteúdo | Listar os arquivos internos (`ls`) |
| **w** | Write (Escrita) | **2** | Alterar o conteúdo | Criar/Deletar arquivos na pasta |
| **x** | Execute (Execução) | **1** | Rodar como programa | Entrar na pasta (`cd`) |

---

## 3. O Comando `chmod` (Change Mode)
Usado para alterar as permissões. Existem duas formas de usar:

### A. Modo Simbólico (Letras)
Útil para adicionar ou remover uma permissão específica.
* `chmod u+x arquivo.sh` (Adiciona execução para o dono)
* `chmod g-w arquivo.txt` (Remove escrita do grupo)
* `chmod a+r arquivo.txt` (Dá leitura para todos - *all*)

### B. Modo Numérico (Octal) - Mais Comum em Backend
Soma-se os valores (4, 2, 1) para cada grupo.



* **7 (4+2+1):** Permissão total (rwx)
* **6 (4+2):** Leitura e Escrita (rw-)
* **5 (4+1):** Leitura e Execução (r-x)
* **4:** Apenas Leitura (r--)

**Exemplos Clássicos:**
* `chmod 755 script.sh` -> Dono faz tudo, os outros só lêem e executam.
* `chmod 644 foto.jpg` -> Dono lê/escreve, os outros só lêem.
* `chmod 400 chave.pem` -> Apenas o dono lê (comum para chaves SSH).

---

## 4. O Comando `chown` (Change Owner)
Muda o dono ou o grupo de um arquivo/diretório.

* **Mudar apenas o dono:**
  `sudo chown usuario arquivo.txt`
* **Mudar o dono e o grupo simultaneamente:**
  `sudo chown usuario:grupo pasta/`
* **Mudar recursivamente (em todos os arquivos dentro de uma pasta):**
  `sudo chown -R deploy:www-data public_html/`

---

## 5. Dicas de Ouro para Desenvolvedores
1.  **Pastas vs Arquivos:** Para entrar em uma pasta via `cd`, você **precisa** da permissão de execução (`x`).
2.  **Scripts Rails/Ruby:** Se você criou um script e o terminal diz `Permission denied`, o comando mágico costuma ser `chmod +x nome_do_arquivo.rb`.
3.  **Segurança:** Evite ao máximo o uso de `chmod 777`. Isso dá permissão total para qualquer pessoa no sistema, o que é um risco enorme de segurança.