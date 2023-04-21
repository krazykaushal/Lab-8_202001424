# <pre> IT 314 - Software Engineering </pre> 
### Lab 8 : Unit Testing with JUnit
## - Student Name : Kaushal Patel
## - Student ID: 202001424
---

### **Aim**: The goal of this lab is to learn how to use JUnit to write unit tests for Java programs.

### **Tools Used:** Eclipse and JUnit 4

- Created a new Eclipse project named ```Lab8_202001424```, and within the project create a package named myPackage.
![image](https://user-images.githubusercontent.com/75678291/233597132-5254c500-f2a0-474a-a3ee-31e762ab3643.png)

- Created a class for a Boa.
![image](https://user-images.githubusercontent.com/75678291/233597813-ae8e430b-034d-44bb-a9ea-b623dcee1502.png)

- Created Junit Test case named ***TestBoa***. Added ```private Boa jen;``` and ```private Boa ken;``` above @Before.
![image](https://user-images.githubusercontent.com/75678291/233601975-fc535916-cc2d-4d7e-97a3-a26a6a6f8cab.png)

- Testing ***isHealthy*** method with the help of ```testIsHealthy()``` method. Testing ***fitsInCage*** method with the help of ```testFitsInCage()``` method.

  - All test cases passed:
![image](https://user-images.githubusercontent.com/75678291/233603531-853330a7-b19d-473f-a07b-119466ab163a.png)

  - Detects error in case of wrong test case:
![image](https://user-images.githubusercontent.com/75678291/233603596-3e47e8dc-8450-49f2-8e22-4d82d5622f2f.png)
![image](https://user-images.githubusercontent.com/75678291/233603915-45c79596-9189-4a35-8ef3-033fec0b3e8f.png)


- Add a new method ```lengthInInches()``` to the Boa class:
![image](https://user-images.githubusercontent.com/75678291/233604448-3e45ce6f-9eb5-4be6-9f69-18ff9627e427.png)

- Testing ```lengthInInches()``` method.

  - All testcases passed:
  ![image](https://user-images.githubusercontent.com/75678291/233605796-41bc736a-b042-41bf-95da-b00d6efa7cb2.png)
  - Detects error in case of wrong test case:
  ![image](https://user-images.githubusercontent.com/75678291/233606008-88dd908c-fcee-4442-80c0-39669d33d546.png)

## Codes Below:

  ### Boa.java:
  ```java
  package myPackage;

// represents a boa constrictor
public class Boa {
	private String name;
	private int length; // the length of the boa, in feet
	private String favoriteFood;
	
	public Boa (String name, int length, String favoriteFood){
		this.name = name;
		this.length = length;
		this.favoriteFood = favoriteFood;
	}
	// returns true if this boa constrictor is healthy
	public boolean isHealthy(){
		return this.favoriteFood.equals("granola bars");
	}
	// returns true if the length of this boa constrictor is
	// less than the given cage length
	public boolean fitsInCage(int cageLength){
		return this.length < cageLength;
	}
	
	//produces the length of the Boa in inches
	
	public int lengthInInches() {
		return this.length * 12;
	}
}
  ```
  
  ### TestBoa.java
  ```java
  package myPackage;

import static org.junit.Assert.*;


import org.junit.Before;
import org.junit.Test;

public class TestBoa {
	
	private Boa jen;
	private Boa ken;

	@Before
	public void setUp() throws Exception {
		jen = new Boa("Jennifer",2 , "grapes");
		ken = new Boa("Jennifer", 3, "granola bars");
	}


	@Test
	public void testIsHealthy() {
		assertEquals(false,jen.isHealthy());
		assertEquals(true, ken.isHealthy());
	}

	@Test
	public void testFitsInCage() {
		assertEquals(true,jen.fitsInCage(7));
		assertEquals(true, ken.fitsInCage(5));
	}
	
	@Test
	public void testlengthInIncher() {
		assertEquals(24, jen.lengthInInches());
		assertEquals(36, ken.lengthInInches());
	}

}

  ```
