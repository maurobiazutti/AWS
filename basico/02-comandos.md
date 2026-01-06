# Guia de Comandos Essenciais do Linux

Este guia cobre os comandos fundamentais para navegação e manipulação de arquivos via terminal (CLI).

---

## 1. Navegação no Sistema
Antes de manipular arquivos, você precisa saber onde está e como se mover.

| Comando | Descrição | Exemplo de Uso |
| :--- | :--- | :--- |
| `pwd` | Exibe o caminho completo do diretório atual. | `pwd` |
| `ls` | Lista arquivos e diretórios. | `ls -la` (lista tudo, incluindo ocultos e detalhes) |
| `cd` | Entra em um diretório. | `cd Documents/projetos` |
| `cd ..` | Volta um nível na hierarquia de pastas. | `cd ..` |

---

## 2. Manipulação de Arquivos e Pastas
Comandos para criar, mover e remover elementos do sistema.



* **`touch`**: Cria um arquivo vazio ou atualiza a data de modificação.
    * *Exemplo:* `touch notas.txt`
* **`mkdir`**: Cria uma nova pasta (diretório).
    * *Exemplo:* `mkdir novo_projeto`
* **`cp`**: Copia arquivos ou diretórios.
    * *Exemplo:* `cp arquivo.txt copia_arquivo.txt`
    * *Dica:* Use `cp -r` para copiar pastas inteiras.
* **`mv`**: Move ou renomeia arquivos/pastas.
    * *Exemplo (Mover):* `mv foto.jpg Imagens/`
    * *Exemplo (Renomear):* `mv nome_antigo.txt nome_novo.txt`
* **`rm`**: Remove arquivos. **Cuidado: Não há lixeira no terminal!**
    * *Exemplo:* `rm arquivo.txt`
    * *Dica:* Use `rm -rf` para forçar a exclusão de pastas (use com extrema cautela).

---

## 3. Visualização de Conteúdo
Para ler o que está dentro dos arquivos sem precisar abrir um editor de texto.

* **`cat`**: Exibe todo o conteúdo do arquivo de uma vez no terminal.
    * *Uso:* `cat config.conf`
* **`less`**: Abre o arquivo para leitura permitindo rolar (melhor para arquivos grandes).
    * *Uso:* `less log_do_sistema.log` (aperte `q` para sair).
* **`head`**: Exibe as primeiras 10 linhas de um arquivo.
    * *Uso:* `head lista.txt`
* **`tail`**: Exibe as últimas 10 linhas de um arquivo.
    * *Uso:* `tail -f logs.txt` (o `-f` mantém o terminal seguindo o arquivo em tempo real, ótimo para monitorar logs).

---

## 4. Comandos Complementares (Bônus Importantes)
Como você está estudando para o nível pleno e foca em backend, estes são indispensáveis:

| Comando | Função | Por que é importante? |
| :--- | :--- | :--- |
| `grep` | Busca texto dentro de arquivos. | `grep "erro" log.txt` ajuda a achar bugs rápido. |
| `find` | Busca arquivos no sistema. | Localizar aquele script perdido. |
| `chmod` | Altera permissões de arquivos. | Necessário para tornar scripts executáveis (`chmod +x`). |
| `sudo` | Executa comandos com privilégios de root. | Instalação de pacotes e alteração de arquivos do sistema. |
| `history` | Mostra os últimos comandos digitados. | Útil para repetir um comando complexo que você esqueceu. |

---

### Dica de Produtividade:
Sempre utilize a tecla **TAB** enquanto digita o nome de uma pasta ou arquivo. O terminal completará o nome automaticamente para você, evitando erros de digitação e economizando tempo.