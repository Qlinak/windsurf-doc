# Set Up a Fullstack Backend: Prisma + NestJS

This workflow will:
- Take a user story and a target project directory as input
- Set up a Prisma database schema and run migration
- Scaffold a NestJS backend application organized by Domain-Driven Design (DDD) layers
- Ensure maintainability, scalability, and testability

## Steps

1. **Print out the following reminders in the terminal**
	 run
	  ```sh
	  echo "please make sure you have your .env file set up in the project root directory"
	  ```

2. **Read the user story and project directory path**
   - Input: User story (text), project directory (path)
  
3. **Look for .env file**
   - check that if an .env file exist in the project root directory, the .env file should contains the following as examples: 
     ```env
     DATABASE_URL=postgresql://user:pass@host:port/db
     JWT_SECRET=your_jwt_secret
     JWT_EXPIRES_IN=3600s
     ```

4. **Set up Prisma DB schema and run migration**
   - Parse the user story to derive the Prisma schema
   - Ensure the `prisma` folder exists in the project directory
   - Write the schema to `prisma/schema.prisma`
   - Ensure `.env` contains a valid `DATABASE_URL`
   - Run migration:
     ```sh
     npx prisma migrate dev --name init
     ```
   - Generate Prisma client:
     ```sh
     npx prisma generate
     ```
    - Report to me what have you done and what do you plan to do base on the current workflow

5. **Set up NestJS backend scaffold**
   - Inside the project directory, ensure the following DDD-based structure:
     - `src/presentation/` (controllers)
     - `src/application/` (services/use-cases)
     - `src/domain/` (entities, value objects)
     - `src/persistence/` (repositories, Prisma client setup)
     - `src/infrastructure/` (providers, middleware, authentication)
    -  Report to me what have you done and what do you plan to do base on the current workflow

6. **Wire up the layers**
   - Use Prisma client in repository implementations for DB access
   - In `infrastructure/`, add JWT strategy, bearer authentication middleware, and related providers
   - In `presentation/`, add authentication controller for login/register endpoints
   - Report to me what have you done and what do you plan to do base on the current workflow

7. **Install essential dependencies**
   - Run:
     ```sh
     npm install @nestjs/config @prisma/client prisma @nestjs/jwt passport-jwt passport @nestjs/passport bcryptjs
     ```
    - Report to me what have you done and what do you plan to do base on the current workflow

8. **Set up unit testing with Jest (in JavaScript)**
   - In any module (e.g., `src/application/`), add a file like `example.service.spec.js`:
     ```js
     const { Test, TestingModule } = require('@nestjs/testing');
     const { ExampleService } = require('./example.service');

     describe('ExampleService', () => {
       let service;

       beforeEach(async () => {
         const module = await Test.createTestingModule({
           providers: [ExampleService],
         }).compile();
         service = module.get(ExampleService);
       });

       it('should be defined', () => {
         expect(service).toBeDefined();
       });
     });
     ```
   - (Do not run the test immediately after setup; just remind the user that you have set it up)
   - Report to me what have you done and what do you plan to do base on the current workflow

9. **Print directory tree for verification**
   - After running the scaffold, print the directory tree to verify structure:
     ```sh
     tree [project-name]
     ```

---

## Example Usage

Suppose your user story is:
> As a user, I can register and log in with email and password, and create posts.

The workflow will create:
- `prisma/schema.prisma` (from user story)
- `src/domain/user.entity.ts`, `src/domain/post.entity.ts`
- `src/application/user.service.ts`, `src/application/post.service.ts`
- `src/presentation/user.controller.ts`, `src/presentation/post.controller.ts`
- `src/persistence/user.repository.ts`, `src/persistence/post.repository.ts`
- `src/infrastructure/` for providers/middleware/authentication

---

## Notes
- This workflow assumes you have Node.js and npm installed.
- For more complex user stories, refine the models and services as needed.
- You can extend the scaffold by adding modules, DTOs, guards, etc.
