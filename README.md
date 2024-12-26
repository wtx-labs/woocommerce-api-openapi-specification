# woocommerce-api-client-java
The WooCommerce REST API Client for Java provides easy access to the features of the e-commerce platform's API.

The client supports the WooCommerce REST API in th latest v3 version.

---

> ⚠️ **Note: This is a development version!**
> 
> The API client is under development and will be gradually expanded to cover the key API functionalities of the commerce engine.

---


## Setup
1. Download this project and build it to create a new artifact in the local Maven repository - use simple command:
```
mvn clean install
```
2. After a successful build, you can use the following artifact as a dependency in your Java project:
wc-api-java is available on maven central:
```xml
<dependency>
    <groupId>wtx.woocommerce</groupId>
    <artifactId>woocommerce-api-client</artifactId>
    <version>0.1.0</version>
</dependency>
```

## Usage
Below is an example usage of the WooCommerceApiClient:

```java
package wtx.woocommerce;

import java.util.List;

import wtx.woocommerce.api.client.CustomersApi;
import wtx.woocommerce.api.client.invoker.ApiException;
import wtx.woocommerce.api.client.model.Customer;

public class WooCommerceApiClientUsageDemo {

    public static void main(String[] args) {

        System.out.println(">>> Start running the WooCommerceApiClientUsageDemo...");

        // Use WooCommerceApiClient(true) if you need to log API communication messages.
        WooCommerceApiClient apiClient = new WooCommerceApiClient();

        // TODO: Set your host and credentials!
        apiClient.setBasePath("https://your-woocommerce-shop.com/wp-json/wc/v3");
        apiClient.setUsername("TODO_SET_API_USERNAME");
        apiClient.setPassword("TODO_SET_API_PASSWORD");

        CustomersApi customersApi = new CustomersApi(apiClient);

        try {

            List<Customer> customers = customersApi.listAllCustomers(null, null, null, null, null, null, null, null, null, null, null, null, null);

            // Example list of customer emails:
            for (Customer customer : customers) {
                System.out.println("Customer: " + customer.getEmail());
            }

        } catch (ApiException e) {
            System.err.println("Error occurred during API call: " + e);
        }

        System.out.println("<<< The WooCommerceApiClientUsageDemo has been finished.");

    }

}
```
## Let's stay in touch!
The client will be continuously developed to incorporate new features and improvements.
See you soon :)
