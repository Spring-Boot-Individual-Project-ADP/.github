## Individual Spring Boot Capstone


**Due to time constraints, while dockerfiles have been created for the account server, authentication server, and data server, it is not currently possible to test the whole project with just these docker containers. Therefore, please run the projects locally if necessary.**

Implemented features:
* Can register a new account, or create a token with credentials that have already been stored
* Can use the frontend (or Postman) to get, create, update, and delete customers
* Can use the frontend (or Postman) to get, create, update, and delete events
* Can use *Postman (only)* to get, create, update, and delete registrations

In order to test the backend, you can download the Postman requests collection and then export that into Postman.

------------------------------
### Instructions

* Clone Account Server, Data Server, and Vite App repositories (not React App!)
* Within Account Server repo
  * Setup docker network
    * `docker network create capstone-network`
  * Build docker image
      * `docker build -t account-server-image .`
  * Run container
    * `docker run -d --name account-server --network capstone-network -p 8081:8081 -e IS_DOCKER=true account-server-image`
* Within Data Server repo
  * Build docker image
    * `docker build -t data-server-image .`
  * Run container
    * `docker run -d --name data-server --network capstone-network -p 8080:8080 data-server-image`
* Within Vite App repo
  * Build docker image
    * `docker build -t vite-app-image . `
  * Run container
    * `docker run -d --name vite-app --network capstone-network -p 5173:5173 -e IS_DOCKER=true vite-app-image`
* Go to [http://localhost:5173/customers](http://localhost:5173/customers) to try out the frontend!



### Potential issues
When building the docker image for Data Server or Account Server, if you encounter an issue with the step `RUN ./gradlew bootJar`, simply convert the line separator in **gradlew** to **LF** and then try again. This can be done by opening the file in IntelliJ or VScode, clicking on CRLF on the bottom right of the editor, and then selecting LF.

<!--

**Here are some ideas to get you started:**

🙋‍♀️ A short introduction - what is your organization all about?
🌈 Contribution guidelines - how can the community get involved?
👩‍💻 Useful resources - where can the community find your docs? Is there anything else the community should know?
🍿 Fun facts - what does your team eat for breakfast?
🧙 Remember, you can do mighty things with the power of [Markdown](https://docs.github.com/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
-->
