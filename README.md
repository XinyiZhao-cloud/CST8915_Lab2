# CST8915 Lab 2: Refactoring for 12-Factor Compliance

**Student Name**: Xinyi Zhao  
**Student ID**: 040953633  
**Course**: CST8915 Full-stack Cloud-native Development  
**Semester**: Winter 2026  

---

## Demo Video

🎥 https://youtu.be/bf9tPZXii20

---
## Repo Links
https://github.com/XinyiZhao-cloud/product-service    
https://github.com/XinyiZhao-cloud/store-front    
https://github.com/XinyiZhao-cloud/order-service   

## Technical Explanations

### What changes did you make to the order-service and product-service to comply with the Configurations and Backing Services factors of the 12-Factor App methodology?

For both order-service(Node.js) and product-service(Rust), I configure via environment variables instead of hard-coded values.  Each service supports a .env file for local/dev convenience, but the real source is the process environment at runtime. This aligns with Twelve-Factor-Configuration by keeping config out of the codebase, and supports Backing Services by treating dependencies that use RabbitMQ as attachable resources via environment-provided connection details rather than embedded addresses. 

### Why is it important to use environment variables instead of hard-coding configurations in your application?

Environment variables make the same codebase portable across environments such as local, VM and different regions without changing the source code. This approach improves safety and flexibility by avoiding accidental deployment of incorrect values (such as localhost) and allows endpoints, ports, or credentials to be updated by changing deployment settings and restarting the service instead of editing and redeploying code.

### Why is it important to have separate repositories for each microservice? How does this help maintain the independence and scalability of each service?

Separate repositories keep microservices independent. Each service can deploy on its own without being coupled to unrelated changes in other services. This improves maintainability by reducing merge conflicts and simplifying ownership, and it supports scalability by allowing individual services to be scaled, optimized, or updated based on their own workload and requirements.

---

## Challenges and Learnings (Optional)

Due to limitations of the Azure for Students subscription, I was restricted to a maximum of six vCPUs per region. This was resolved by deploying one of the virtual machines in a different region (East US). I also encountered issues fetching data from the product-service, which were resolved by ensuring that the code running on the virtual machines matched the configuration in the GitHub repositories and by correctly rebuilding the store-front after environment variable changes.


---

## Acknowledgments

ChatGPT was used to assist with troubleshooting technical issues and improving grammar, clarity, and unnatural expressions in the documentation.

