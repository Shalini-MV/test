**Customer-Billing-and-Rewards-Service**

**Technical Specifications**

JDK Version: 11
Data Storage: H2

**Project Setup Guidelines**

Download and set up the Maven project.
Open git bash and change to the directory customer-rewards-service.
Use the ls command to list all files within the directory.
Execute mvn clean install to build the project.
To launch the application, run docker-compose up from git bash.

**Verifying the Application**

Health Check: App Health Status
API Documentation: Swagger UI
Project Artifacts Folder

The project-artifacts folder contains:

Class and Sequence Diagrams
JSON files for Customers, Transactions, and Monthly and Quarterly Reports. These are obtainable through the Swagger UI.

**Domain Models**

Customer: Houses basic customer information.
Transaction: Contains monthly transaction data, and has a Many-to-One relationship with Customer. Reward points are calculated before saving a transaction.

**API Controllers**

CRUD operations are available via CustomerController and TransactionController.
RewardSummaryController has APIs for both monthly and quarterly reports, accepting 'month' and 'quarter' as parameters.

**Performance**

The quarterly report functionality utilizes parallelStream for efficiency.
Performance should be benchmarked, especially for handling large datasets.

**Service Architecture Considerations**

For complex models involving more tables, the service could be split into customer-service and billing-service.
**Data Persistence and Caching**

Reports are not saved to the database by default. This can be updated if needed.
Consider using local or centralized caching to avoid repeated database calls for generating reports.
Note: DTO transformation is not implemented in this project.

**API Endpoints and Examples**

Create Customer Endpoint: POST Example Request and Response
List All Customers: GET Example Response
Create Transaction Endpoint: POST Example Request and Response
Monthly Reports: GET Example Response
Quarterly Reports: GET Example Response

**Additional Information**

After the app is active, you can view all available endpoints at: Swagger UI
For more details like diagrams and endpoint responses, refer to the project-artifacts directory.
