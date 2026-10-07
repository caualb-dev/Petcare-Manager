# 🐾 PetCare Manager

<div align="center">

![Status](https://img.shields.io/badge/Status-Concluído-success?style=for-the-badge)
![Java](https://img.shields.io/badge/Java_21-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot_3.5-6DB33F?style=for-the-badge&logo=spring-boot&logoColor=white)
![Spring Security](https://img.shields.io/badge/Spring_Security_JWT-6DB33F?style=for-the-badge&logo=spring-security&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)
![Hibernate](https://img.shields.io/badge/Hibernate_JPA-59666C?style=for-the-badge&logo=hibernate&logoColor=white)
<br>
![React](https://img.shields.io/badge/React_19-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![Vite](https://img.shields.io/badge/Vite_6-646CFF?style=for-the-badge&logo=vite&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS_v4-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)

<p align="center">
  <b>Sistema Full-Stack completo para gestão moderna de clínicas veterinárias e hospitais pet.</b><br>
  Construído com arquitetura robusta em microsserviço/monorepo, segurança corporativa por níveis de acesso (RBAC), API RESTful escalável e interface vibrante no padrão <i>Neo-Playful Design</i>.
</p>

</div>

---

## 📖 Sobre o Projeto

O **PetCare Manager** foi idealizado e desenvolvido como uma solução completa para informatizar e otimizar as operações diárias de clínicas veterinárias. O sistema cobre desde a recepção e cadastro de tutores/pacientes até o atendimento clínico especializado, controle de consultas, prontuário médico eletrônico e gestão de equipe.

O projeto é organizado no formato **Monorepo**, contendo:
* **Backend:** API RESTful robusta desenvolvida em **Java 21** e **Spring Boot 3**, com autenticação stateless via **JWT**, controle de acesso **RBAC** e persistência relacional no **PostgreSQL**.
* **Frontend:** Single Page Application (SPA) reativa e dinâmica desenvolvida em **React 19**, **TypeScript** e **Vite**, com estilização moderna através do **Tailwind CSS**.

---

## 🎨 Identidade Visual (Neo-Playful / Neo-Brutalist)

A interface gráfica adota uma identidade visual única baseada na estética **Neo-Playful** (uma derivação amigável do Neo-Brutalismo):
* 📐 **Bordas Marcantes:** Linhas pretas sólidas (`border-2 border-black`) trazendo definição e contraste.
* 📦 **Sombras Deslocadas:** Sombras duras sem desfoque (`shadow-[4px_4px_0px_0px_#000]`) conferindo sensação física e tátil aos cards e botões.
* 🌈 **Paleta Vibrante:** Combinações de tons pastéis e cores enérgicas (Ciano `#22d3ee`, Bege/Areia, Amarelo e Rosa) que reduzem o cansaço visual e tornam o uso do sistema agradável tanto para recepcionistas quanto para veterinários.

---

## 🏛️ Arquitetura e Tecnologias

### ⚙️ Back-end (API REST)
* **Linguagem & Plataforma:** Java 21 (LTS)
* **Framework:** Spring Boot 3.5.14
* **Segurança:**
  * **Spring Security 6** com gerenciamento de sessão Stateless
  * Autenticação e autorização via **JWT (JSON Web Token)** com biblioteca Auth0 (`java-jwt 4.5.2`)
  * Algoritmo de criptografia **BCrypt** para proteção de senhas
  * Filtro customizado de requisições (`OncePerRequestFilter`) com validação de cabeçalho `Authorization: Bearer <token>`
* **Persistência & Dados:**
  * **PostgreSQL** para armazenamento relacional confiável
  * **Spring Data JPA** e **Hibernate ORM** com mapeamento de relacionamentos complexos (`@OneToMany`, `@ManyToOne`, `@ManyToMany`)
  * Inicialização automática do schema e carga de dados semente (`data.sql` e `DataSeeder`)
* **Notificação & E-mail:**
  * `spring-boot-starter-mail` para recuperação de senhas via SMTP seguro
  * Integração com Resend API
* **Produtividade & Qualidade:**
  * **Lombok** para redução de código boilerplate
  * **Bean Validation** (`jakarta.validation`) para integridade das entradas de dados
  * Tratamento global de exceções centralizado (`@RestControllerAdvice`)

### 💻 Front-end (Web SPA)
* **Linguagem & Framework:** React 19 com TypeScript
* **Build Tool:** Vite 6
* **Estilização:** Tailwind CSS v4, `tailwind-merge` e `clsx`
* **Roteamento:** React Router DOM (v7) com guardas de autenticação e controle de permissões por perfil
* **Ícones:** Lucide React
* **Comunicação:** Fetch API com interceptação e injeção dinâmica de token JWT

---

## 🔐 Controle de Acesso por Perfil (RBAC)

O sistema implementa **Role-Based Access Control** em todas as camadas (banco de dados, filtros de segurança da API e roteamento de telas no frontend):

| Perfil | Permissões & Atribuições |
|---|---|
| 👑 **ADMIN (Administrador)** | Acesso irrestrito a todo o sistema. Gestão completa de usuários (criação, edição, inativação), gerenciamento da equipe veterinária, visualização e auditoria geral. |
| 📋 **FUNCIONARIO (Recepção)** | Cadastro, consulta e edição de **Clientes (Tutores)** e **Pets**; Agendamento e cancelamento de consultas; Acesso ao catálogo de serviços e informações gerais. |
| 🩺 **VET (Veterinário)** | Acesso à agenda de consultas; Atendimento clínico com preenchimento de prontuário, registro de diagnósticos, sintomas observados e prescrição de medicamentos; Finalização de consultas. |

---

## 🗄️ Modelo de Dados & Entidades Principais

* **`Usuario`:** Autenticação, e-mail, senha criptografada (BCrypt), status (`ativo`) e cargo (`ADMIN`, `FUNCIONARIO`, `VET`).
* **`Veterinario`:** Dados do médico veterinário, CRMV, especialidade e vínculo com o usuário do sistema.
* **`Cliente`:** Informações cadastrais do tutor (nome, CPF, telefone, endereço, e-mail).
* **`Pet`:** Paciente veterinário (nome, espécie, raça, data de nascimento, peso e vínculo com o tutor).
* **`Consulta`:** Registro do atendimento, data/horário, status (`AGENDADA`, `EM_ANDAMENTO`, `CONCLUIDA`, `CANCELADA`), motivo, diagnóstico e orientações.
* **`Sintoma`:** Catálogo de sintomas clínicos pré-cadastrados (Febre, Apatia, Vômito, Diarreia, etc.).
* **`Medicamento`:** Catálogo farmacológico pré-cadastrado com dosagens padrão (Amoxicilina, Dipirona, Prednisolona, etc.).

---

## 📡 Visão Geral da API REST

### Autenticação & Recuperação de Senha
* `POST /api/auth/login` - Autentica usuário e retorna JWT com dados do perfil *(Público)*
* `POST /api/auth/recuperar-senha` - Solicita link de recuperação por e-mail *(Público)*
* `POST /api/auth/redefinir-senha` - Altera a senha utilizando o token de recuperação *(Público)*

### Gestão de Usuários
* `GET /api/usuarios` - Lista todos os usuários cadastrados *(ADMIN)*
* `POST /api/usuarios` - Cadastra novo usuário no sistema *(ADMIN)*
* `PUT /api/usuarios/{id}` - Atualiza dados do usuário *(ADMIN)*
* `PATCH /api/usuarios/{id}/inativar` - Inativação lógica do usuário *(ADMIN)*

### Equipe Veterinária
* `GET /api/veterinarios` - Lista os médicos veterinários *(ADMIN, FUNCIONARIO)*
* `POST /api/veterinarios` - Cadastra veterinário com CRMV *(ADMIN)*
* `PUT /api/veterinarios/{id}` - Atualiza cadastro veterinário *(ADMIN)*

### Clientes (Tutores) & Pets
* `GET /api/clientes` / `POST /api/clientes` - Gerenciamento de tutores *(ADMIN, FUNCIONARIO)*
* `GET /api/pets` / `POST /api/pets` - Gerenciamento de animais *(ADMIN, FUNCIONARIO, VET)*
* `GET /api/pets/cliente/{clienteId}` - Lista animais pertencentes a um tutor *(ADMIN, FUNCIONARIO, VET)*

### Consultas & Atendimento Clínico
* `GET /api/consultas` - Lista consultas com filtros de data e status *(Autenticado)*
* `POST /api/consultas` - Agenda nova consulta *(ADMIN, FUNCIONARIO)*
* `PUT /api/consultas/{id}` - Atualização e preenchimento de prontuário *(Autenticado)*
* `GET /api/sintomas` - Lista catálogo de sintomas *(Autenticado)*
* `GET /api/medicamentos` - Lista catálogo de medicamentos *(Autenticado)*

---

## 📁 Estrutura do Monorepo

```text
Petcare-Manager/
├── backend/
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/com/petcare/api/
│   │   │   │   ├── controller/      # Endpoints RESTful
│   │   │   │   ├── dto/             # Request & Response Data Transfer Objects
│   │   │   │   ├── exception/       # GlobalExceptionHandler e Exceptions de domínio
│   │   │   │   ├── model/           # Entidades JPA e Enums
│   │   │   │   ├── repository/      # Interfaces Spring Data JPA
│   │   │   │   ├── security/        # Filtro JWT, SecurityFilterChain e BCrypt
│   │   │   │   └── service/         # Regras de negócio e DataSeeder
│   │   │   └── resources/
│   │   │       ├── data.sql         # Carga inicial de sintomas e medicamentos
│   │   │       └── application.properties.example
│   ├── pom.xml                      # Dependências Maven
│   └── Dockerfile
├── frontend/
│   ├── src/
│   │   ├── components/              # Componentes reutilizáveis (Card, Button, Modal, Sidebar)
│   │   ├── pages/                   # Telas (Dashboard, Clientes, Pets, Consultas, Equipe, Login)
│   │   ├── lib/                     # Configurações de API e Auth Helpers
│   │   ├── App.tsx                  # Roteador principal e rotas protegidas
│   │   └── main.tsx
│   ├── tailwind.config.js           # Tema e tokens de design
│   ├── package.json
│   └── vite.config.ts
├── .gitignore                       # Ignora target/, node_modules/ e credenciais locais
└── README.md
```

---

## 🚀 Como Executar o Projeto Localmente

### Pré-requisitos
* **Java 21** instalado (`java -version`)
* **Node.js 18+** e **npm** instalados (`node -v` e `npm -v`)
* **PostgreSQL** instalado e em execução na porta `5432`

---

### 1️⃣ Configuração do Banco de Dados (PostgreSQL)

Abra o seu terminal e crie o usuário e a base de dados:

```bash
# Acessar o postgres e definir a senha padrão
sudo -u postgres psql -c "ALTER USER postgres PASSWORD 'petcare2712';"

# Criar a base de dados do projeto
sudo -u postgres psql -c "CREATE DATABASE petcare_db;"

# Garantir permissões completas no schema public (PostgreSQL 15+)
sudo -u postgres psql -d petcare_db -c "GRANT ALL ON SCHEMA public TO postgres;"
```

---

### 2️⃣ Executando o Back-end (Spring Boot)

1. Acesse o diretório do backend:
   ```bash
   cd backend
   ```
2. Crie ou configure seu arquivo `src/main/resources/application.properties` (se necessário, copie do exemplo):
   ```bash
   cp src/main/resources/application.properties.example src/main/resources/application.properties
   ```
3. Execute a aplicação utilizando o Maven Wrapper:
   ```bash
   ./mvnw spring-boot:run
   ```
4. A API estará pronta e respondendo em: `http://localhost:8080/api`

> 💡 **Usuário Administrador Automático:**
> Na primeira inicialização, a API cria automaticamente o primeiro administrador do sistema:
> * **Usuário:** `admin`
> * **Senha:** `admin123`

---

### 3️⃣ Executando o Front-end (React + Vite)

1. Em um novo terminal, acesse o diretório do frontend:
   ```bash
   cd frontend
   ```
2. Instale as dependências:
   ```bash
   npm install
   ```
3. Inicie o servidor de desenvolvimento:
   ```bash
   npm run dev
   ```
4. Acesse a aplicação no seu navegador: `http://localhost:5173`

---

## 👥 Autores & Colaboradores

Projeto desenvolvido em colaboração:

<table>
  <tr>
    <td align="center">
      <a href="https://github.com/caualb-dev">
        <img src="https://github.com/caualb-dev.png" width="100px;" alt="Cauã Albuquerque"/><br>
        <sub><b>Cauã Albuquerque</b></sub>
      </a><br>
      <sub><b>Arquiteto & Desenvolvedor Backend</b></sub><br>
      <sub>Java 21 • Spring Boot • Spring Security • JWT • PostgreSQL • JPA</sub>
    </td>
    <td align="center">
      <a href="https://github.com/leticiamls">
        <img src="https://github.com/leticiamls.png" width="100px;" alt="Letícia"/><br>
        <sub><b>Letícia</b></sub>
      </a><br>
      <sub><b>Desenvolvedora Frontend & UI/UX</b></sub><br>
      <sub>React • TypeScript • Tailwind CSS • Vite • Neo-Playful UI</sub>
    </td>
  </tr>
</table>

---

## 📄 Licença

Este projeto foi desenvolvido para fins educacionais e de portfólio. Sinta-se à vontade para explorar, clonar e utilizar como referência!
