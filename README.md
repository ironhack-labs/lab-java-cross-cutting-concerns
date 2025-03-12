![logo_ironhack_blue 7](https://user-images.githubusercontent.com/23629340/40541063-a07a0a8a-601a-11e8-91b5-2f13e4e6b441.png)

# LAB Java | Feign Interceptors & Cross-Cutting Concerns

## Introduction

In this lab, you will build a standalone Spring Boot application that demonstrates how to centralize cross-cutting concerns using a custom Feign interceptor. Your interceptor will be responsible for tasks such as adding an authentication header, injecting a correlation ID, and logging details of every outbound HTTP request. Rather than following a detailed, step-by-step recipe, you are expected to design and implement the solution on your own using the concepts discussed in class.

<br />

## Requirements

1. Fork this repo.
2. Clone this repo.
3. Add your instructor and the class graders as collaborators to your repository. If you are unsure who your class graders are, ask your instructor or refer to the day 1 slide deck.
4. In the repository, create a Java project and add the code for the following prompts.

<br />

## Submission

Once you finish the assignment, submit a URL link to your repository or your pull request in the field below.

<br />

## Instructions

### 1. Set Up the Project

- Create a new Spring Boot project using Spring Initializr.
- Include the **Spring Web** and **Spring Cloud OpenFeign** dependencies.
- Configure your application to run on a port of your choice.

### 2. Create a Dummy Remote Service

- Implement a REST controller that simulates an external service by exposing an endpoint named `/remote/message`.
- This endpoint should return a basic text message.
- This endpoint will be used by your Feign client to test outbound requests.

### 3. Define a Feign Client

- Create a Feign client interface to call the dummy remote service at `/remote/message`.
- Configure the Feign client with a fixed URL (for example, pointing to `http://localhost:<port>`).

### 4. Implement the Custom Feign Interceptor

- Implement the `RequestInterceptor` interface in a custom class.
- In the interceptor:
  - Read an authentication token from the application configuration, and if present, add an `Authorization` header.
  - Generate a unique correlation ID for each request and add it to the headers as `X-Correlation-ID`.
  - Log the HTTP method, URL, and headers of the outbound request.
- Ensure that Spring Boot applies this interceptor to all Feign client calls by registering it as a bean in your application context.

### 5. Configure Application Properties

- In your `application.properties`, create a property named `auth.token` to store your sample authentication token.

### 6. Test Your Implementation

- Create a controller endpoint that uses your Feign client to call the dummy remote service.
- Run your application and invoke this new endpoint using a web browser, Postman, or another HTTP client.
- Inspect logs or use a tool like Postman Console, Fiddler, or Wireshark to confirm that:
  - The `Authorization` header is present if the token property is set.
  - The `X-Correlation-ID` header is included.
  - The request details (method, URL, headers) are logged.

### 7. Documentation

- Update your project's `README.md` to include:
  - A brief explanation of your design choices.
  - A summary of your testing process and findings.
  - Answers to questions such as:
    - What benefits does centralizing cross-cutting concerns in a Feign interceptor offer?
    - How do authentication headers and correlation IDs improve your application's reliability and traceability?
    - What challenges did you face, and how might you improve the solution in a real-world scenario?

<br />

## Guidelines & Hints

- **Keep It Modular:** Think about where to place your interceptor class so that Spring Boot automatically registers it.
- **Configuration:** Consider how you can use configuration properties to drive the behavior of your interceptor.
- **Testing:** Focus on verifying that your interceptor works as intended. Use logs and external tools to inspect HTTP requests.
- **Research:** If you’re unsure about any part of the implementation, review the official Spring Cloud OpenFeign documentation and relevant online resources.

<br />

## FAQs

<br>

<details>
  <summary style="font-size: 16px; cursor: pointer; outline: none; font-weight: bold;">I am stuck and don't know how to solve the problem or where to start. What should I do?</summary>

<br> <!-- ✅ -->

If you are stuck in your code and don't know how to solve the problem or where to start, you should take a step back and try to form a clear, straight forward question about the specific issue you are facing. The process you will go through while trying to define this question, will help you narrow down the problem and come up with potential solutions.

For example, are you facing a problem because you don't understand the concept or are you receiving an error message that you don't know how to fix? It is usually helpful to try to state the problem as clearly as possible, including any error messages you are receiving. This can help you communicate the issue to others and potentially get help from classmates or online resources.

Once you have a clear understanding of the problem, you should be able to start working toward the solution.

</details>

<br>

<details>
  <summary style="font-size: 16px; cursor: pointer; outline: none; font-weight: bold;">How do I create a Spring boot project?</summary>

<br> <!-- ✅ -->

Spring boot is a framework for creating stand-alone, production-grade applications that are easy to launch and run. The best way to create a Spring boot project is to use the Spring Initializer website. The website provides a convenient way to generate a basic project structure with all the necessary dependencies and configurations.

- Step 1: Go to [start.spring.io](https://start.spring.io/)
- Step 2: Choose the type of project you want to create, such as Maven or Gradle.
- Step 3: Select the version of Spring Boot you want to use.
- Step 4: Choose the dependencies you need for your project. Some common dependencies include web, jpa and data-jpa.
- Step 5: Click the "Generate" button to download the project files.

Alternatively, you can use an Integrated Development Environment (IDE) such as Eclipse or IntelliJ IDEA. These IDEs have plugins for creating Spring boot projects, making it easy to set up the environment and get started with coding.

 </details>

<br>

<details>
  <summary style="font-size: 16px; cursor: pointer; outline: none; font-weight: bold;">How can I verify the headers of my HTTP requests?</summary>
  <br />
  You can use Postman Console, Fiddler, or Wireshark to inspect the outgoing HTTP requests and confirm the presence of your custom headers.
</details>

<br />

<details>
  <summary style="font-size: 16px; cursor: pointer; outline: none; font-weight: bold;">What if my interceptor isn’t working?</summary>
  <br />
  Ensure that your interceptor class is annotated with `@Component` and located in a package scanned by Spring Boot. Also, check your configuration properties and verify that your Feign client is correctly set up.
</details>

<br />

<details>
  <summary style="font-size: 16px; cursor: pointer; outline: none; font-weight: bold;">How can I debug a failing Feign client request?</summary>
  <br />
  Use logging to output the details of your requests and responses. Additionally, employ network monitoring tools (like Postman Console or Wireshark) to trace HTTP traffic and identify where the request might be failing.
</details>

<br />

<details>
  <summary style="font-size: 16px; cursor: pointer; outline: none; font-weight: bold;">Where can I find more information on advanced DI and Feign interceptors?</summary>
  <br />
  The official Spring Cloud OpenFeign documentation, as well as articles and tutorials on sites like Baeldung and the Spring blog, are excellent resources to further explore these topics.
</details>

<br />

<details>
  <summary style="font-size: 16px; cursor: pointer; outline: none; font-weight: bold;">I am unable to push changes to my repository. What should I do?</summary>

<br> <!-- ✅ -->

If you are unable to push changes to your repository, here are a few steps that you can follow:

1. Check your internet connection: Ensure that your internet connection is stable and working.
1. Verify your repository URL: Make sure that you are using the correct repository URL to push your changes.
1. Check Git credentials: Ensure that your Git credentials are up-to-date and correct. You can check your credentials using the following command:

```bash
git config --list
```

4. Update your local repository: Before pushing changes, make sure that your local repository is up-to-date with the remote repository. You can update your local repository using the following command:

```bash
git fetch origin
```

5. Check for conflicts: If there are any conflicts between your local repository and the remote repository, resolve them before pushing changes.
6. Push changes: Once you have resolved any conflicts and updated your local repository, you can try pushing changes again using the following command:

```bash
git push origin <branch_name>
```

</details>
