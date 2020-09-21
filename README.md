# grokonez-springboot-mongodb-restapi - NO NEED FOR CREATING CONTROLLER

## Dependencies
  - Spring REST Repoositories
  - Spring Data MongoDB
## Entity
   ```
   @org.springframework.data.annotation.Id
   private Long Id;
   private String firstName;
   private String lastName;
   private static AtomicLong COUNTER = new AtomicLong(0L);
   
   @PersistenceConstructor
   public Customer() {
    this.id= CUSTOMER.incrementAndGet();
   }
   // getters and setters for String fields
   ```
 ## Repository
  ```
  @RepositoryRestResource(CollectionResourceRel = "customer", path="customer")
  public interface CustomerRepository implements MongoRepository<Customer, Long> {
   List<Customer> findByLastName(@Param("lastName") String lastName);
   // this whole code will create automatic url like http://localhost:8081/customer/search?lastName=
  }
  ```
## Properties
  ```
  spring.data.mongodb.database=grokonez-restapi
  spring.data.mongodb.port=27017
  ```
