# 🎵 Sistema Musical — Desenvolvimento Web (PHP + MySQL)

<p align="center">
  <img src="https://img.shields.io/badge/Curso-Desenvolvimento%20de%20Sistemas-blue?style=for-the-badge&logo=senai" alt="Curso SENAI">
  <img src="https://img.shields.io/badge/Escola-SENAI%20A.%20Jacob%20Lafer-red?style=for-the-badge" alt="SENAI A. Jacob Lafer">
  <img src="https://img.shields.io/badge/PHP-8.x-777BB4?style=for-the-badge&logo=php&logoColor=white" alt="PHP">
  <img src="https://img.shields.io/badge/MySQL-5.7%2B-4479A1?style=for-the-badge&logo=mysql&logoColor=white" alt="MySQL">
</p>

---

## 📌 Sobre o Projeto

O **Sistema Musical** é uma aplicação web completa desenvolvida para a entrega final do curso de **Desenvolvimento de Sistemas** da escola **SENAI A. Jacob Lafer**. 

O sistema permite gerenciar um catálogo de artistas e suas respectivas músicas, oferecendo recursos de login com sessão, criptografia de senhas, CRUDs completos, upload e redimensionamento automático de imagens, integração com links do YouTube e busca com filtros dinâmicos.

---

## 🚀 Funcionalidades

- **🔐 Autenticação & Segurança:**
  - Autenticação com controle de sessão (`PHP Sessions`).
  - Proteção de páginas restritas via middleware (`valida_sessao.php`).
  - Criptografia de senhas no banco de dados utilizando **BCrypt** (`password_hash` / `password_verify`).
  - Proteção contra **SQL Injection** com *Prepared Statements* (`bind_param`) e contra **XSS** via `htmlspecialchars()`.

- **🎤 Gestão de Artistas (CRUD Completo):**
  - Cadastro, listagem, edição e exclusão de artistas.
  - Upload e redimensionamento automático da foto do artista (utilizando a extensão **GD** do PHP).
  - Regra de negócio: impede a exclusão de artistas que possuem músicas vinculadas.

- **🎵 Gestão de Músicas (CRUD Completo):**
  - Cadastro de músicas associadas a um artista (Chave Estrangeira).
  - Upload e tratamento da foto da capa do álbum.
  - Extração e validação do ID de vídeos do YouTube para reprodução rápida.
  - Exclusão do arquivo físico da imagem no servidor (`unlink`) ao remover uma música.

- **🎼 Biblioteca Musical & Filtros Dinâmicos:**
  - Exibição de todo o acervo de músicas cadastradas.
  - Filtros combináveis por **busca geral** (título, álbum ou artista), **artista específico** e **gênero**.
  - Preservação dos parâmetros da busca na URL (`http_build_query`) após ações de edição ou exclusão.

---

## 📂 Estrutura de Arquivos

```text
sistema-musical/
├── styles.css               # Estilização global da aplicação
├── bd.sql                   # Script SQL de criação do banco e tabelas
├── conexao.php              # Conexão MySQLi e verificação do diretório img/
├── geraSenha.php            # Utilitário para geração de hashes BCrypt
├── valida_sessao.php        # Middleware de proteção por autenticação
├── login.php                # Tela de autenticação de usuários
├── logout.php               # Encerramento de sessão e destruição de cookies
├── index.php                # Menu principal do sistema
├── cadastro_artista.php     # CRUD de artistas + upload de foto
├── cadastro_musica.php      # CRUD de músicas + link YouTube + capa do álbum
├── listagem_musicas.php     # Biblioteca musical com filtros de pesquisa
└── img/                     # Pasta para armazenamento das imagens enviadas
```

---

## 🛠️ Tecnologias Utilizadas

- **Frontend:** HTML5, CSS3, JavaScript (Diálogos de confirmação)
- **Backend:** PHP 8.x
- **Banco de Dados:** MySQL / MariaDB
- **Processamento de Imagens:** Extensão PHP GD (*Graphics Draw*)
- **Ambiente Local Recomendado:** XAMPP, WAMP ou Laragon

---

## ⚙️ Como Executar o Projeto

### 1. Pré-requisitos
- Servidor web local com **PHP 8.x** e **MySQL**.
- Extensão **GD** habilitada no arquivo `php.ini` do PHP.

### 2. Instalação e Configuração

1. **Clonar o Repositório:**
   ```bash
   git clone https://github.com/SEU-USUARIO/SEU-REPOSITORIO.git
   ```

2. **Configurar o Banco de Dados:**
   - Acesse o gerenciador de banco de dados (ex: phpMyAdmin em `http://localhost/phpmyadmin`).
   - Execute o script contido no arquivo `bd.sql`.
   - Esse comando criará o banco `sistema_musical_v2`, as tabelas necessárias e o usuário inicial.

3. **Ajustar Credenciais de Conexão:**
   - Se a senha do seu MySQL local for diferente da padrão do SENAI, abra o arquivo `conexao.php` e atualize os campos:
     ```php
     $servername = "localhost";
     $username   = "root";
     $password   = "SuaSenhaAqui";
     $dbname     = "sistema_musical_v2";
     ```

4. **Acessar a Aplicação:**
   - Coloque a pasta do projeto dentro do diretório do seu servidor web (`htdocs` ou `www`).
   - Acesse via navegador: `http://localhost/sistema-musical/login.php`

---

## 🔑 Credenciais de Teste

Para o primeiro acesso ao sistema, utilize a conta padrão pré-cadastrada no banco de dados:

- **Usuário:** `admin`
- **Senha:** `123`

---

## 🛡️ Práticas de Segurança Implementadas

- **BCrypt Hashing:** Senhas nunca são salvas em texto puro.
- **Prepared Statements:** Proteção integral contra injeções de código SQL.
- **Sanitização e Escapamento:** Uso de `intval()` em parâmetros GET e `htmlspecialchars()` na renderização das views.
- **Validação de Uploads:** Verificação de tipo de extensão (`.jpg`, `.jpeg`, `.png`), limitação de tamanho (máximo 5MB) e validação da imagem com `getimagesize()`.

---

<p align="center">
  Desenvolvido para o curso de <strong>Desenvolvimento de Sistemas</strong><br>
  <strong>SENAI A. Jacob Lafer</strong>
</p>
