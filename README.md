# Hibernate-with-MYSQL
Hibernate with mysql configuration


#Create the java project
#Add jar files for hibernate
#Create the Persistent class
#Create the mapping file for Persistent class
#Create the Configuration file
#Create the class that retrieves or stores the persistent object
#Run the application

#employee configuration file:
 
 <hibernate-mapping>
	<class name="com.javatpoint.mypackage.Employee" table="employee">
		<id name="id" column="id">
			<generator class="assigned"></generator>
		</id>

		<property name="firstName"></property>
		<property name="lastName"></property>

	</class>

</hibernate-mapping>  



 #Main class:
 
 	Configuration cfg = new Configuration();
		cfg.configure("hibernate.cfg.xml");// populates the data of the
											// configuration file

		// creating seession factory object
		SessionFactory factory = cfg.buildSessionFactory();

		// creating session object
		Session session = factory.openSession();

		// creating transaction object
		Transaction t = session.beginTransaction();

		Employee e1 = new Employee();
		e1.setId(119);
		e1.setFirstName("sonoo");
		e1.setLastName("jaiswal");

		session.persist(e1);// persisting the object

		t.commit();// transaction is committed
		session.close();

#Hibernate configuration:

<hibernate-configuration>
	<session-factory>
		<property name="hbm2ddl.auto">update</property>
		<property name="dialect">org.hibernate.dialect.MySQLDialect</property>
		<property name="connection.url">jdbc:mysql://localhost/sandy</property>
		<property name="connection.username">root</property>
		<property name="connection.password">sandy</property>
		<property name="connection.driver_class">com.mysql.jdbc.Driver</property>
		<mapping resource="employee.hbm.xml" />
	</session-factory>
</hibernate-configuration>  


    
    #pojo class:
    private int id;  
	  private String firstName,lastName;


