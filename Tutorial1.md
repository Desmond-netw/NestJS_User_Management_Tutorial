# Building a Full-Stack User Management System with NestJS, PostgreSQL, TypeORM, and React

### _Welcome to this step-by-step tutorial for building a full-stack user management system! We will use NestJS for our back-end (with PostgreSQL, TypeORM, Passport for authentication, class-validator for validation, and class-transformer for serialization), and React for our front-end. This tutorial is beginner-friendly, with all steps explained in the logical order of implementation_

## Table of Contents

1. [Introduction to the Stack](#item-1)
2. [Setting Up the Backend with NestJS](#item-2)
    - Installing NestJS CLI
    - Creating a NestJS Project
    - Adding Dependencies
3. [Configuring PostgreSQL & TypeORM](#item-3)
    - Database Creation
    - Global TypeORM Configuration
* Creating the User Module

<a id="item-1"></a>
## Introduction to the Stack
Before we start coding, let's briefly introduce the technologies we'll use and how they fit together:

**NestJS**: A progressive Node.js framework for building efficient server-side applications. It provides a structured way to build scalable backends with TypeScript.

**PostgreSQL**: A powerful open-source relational database. We'll use it to store our user data.

**TypeORM**: An ORM (Object-Relational Mapping) library for TypeScript/JavaScript that integrates well with NestJS, making it easy to manage database tables as TypeScript classes (entities).

**Passport**: A popular authentication middleware for Node.js. We will use Passport's Local Strategy for email/password login and JWT Strategy for protecting routes with JSON Web Tokens.

**class-validator**: A validation library that integrates with NestJS to declaratively validate incoming request data (DTOs). It lets us add decorators like @IsEmail() or @IsNotEmpty() to DTO classes, automatically checking input at runtime.

**class-transformer**: A library for transforming and sanitizing class instances. We will use it with NestJS's serialization interceptor to hide sensitive fields (like passwords) from the responses by using the @Exclude() decorator.

**ReactJS**: Our front-end library of choice, which will interact with the NestJS backend through HTTP requests. We'll create a simple single-page application (SPA) with forms for registration and login, and a protected profile page.

### How they connect

When a user registers or logs in from the React frontend, the app will send HTTP requests to our NestJS API. The NestJS backend will validate and process these requests, interact with the PostgreSQL database via TypeORM, and return responses (like a JWT token or user info). React will then update the UI based on these responses (e.g., storing the JWT and showing the profile data).

With the overview out of the way, let's set up our backend!

 <a id="item-2"></a>
## Setting Up the Backend with NestJS
s
### Creating NestJS Resources in Nx

> [!Warning]
> If you're using Nx, replace any Nest CLI resource generation like nest g resource auth with

Remove [--dry-run] to generate the files:

### Alternative: Installing nestJS CLI
First, ensure you have the NestJS CLI installed globally. The NestJS CLI helps scaffold projects and generate components like modules, services, and controllers.

If you haven't installed it yet, run: 

```sh
npm install -g @nestjs/cli
```
This installs the Nest CLI globally on your system. You can verify the installation by running [nest --version] in the terminal. 

### Creating a NestJS Project
Next, create a new NestJS project. For this tutorial, we'll call it "user-auth-system":