# Lab 8 - 202001271

## Dhruv Patel
## JUnit testing; 21 April, 2023

### Goal of the lab: Goal: The goal of this lab is to learn how to use JUnit to write unit tests for Java programs.


1. Create a new Eclipse project, and within the project create a package.

![1](https://user-images.githubusercontent.com/75672785/233618949-67123651-60f7-4be7-a3a1-5d968bedc0c7.png)
![2](https://user-images.githubusercontent.com/75672785/233618955-6aae6276-7e53-48c8-8f2c-34ceef13b589.png)


2. Created a class in the package - class name - Boa and junit test case file - BoaTest

![4](https://user-images.githubusercontent.com/75672785/233618983-4065e80b-389f-4dff-9dde-1c12c1245710.png)

```java
package lab8_202001271;

//represents a boa constrictor
public class Boa {
	private String name;
	private int length; // the length of the boa, in feet
	private String favoriteFood;

	public Boa(String name, int length, String favoriteFood) {
		this.name = name;
		this.length = length;
		this.favoriteFood = favoriteFood;
	}

	//returns true if this boa constrictor is healthy
	public boolean isHealthy() {
		return this.favoriteFood.equals("granola bars");
	}

	//returns true if the length of this boa constrictor is
	//less than the given cage length
	public boolean fitsInCage(int cageLength) {
		return this.length < cageLength;
	}
}
```

3. Created junit test case for class Boa - BoaTest and for test method stubs, select both isHealthy() and fitsInCage(int).

See the screenshot given below to see the tasks done till now:

![6](https://user-images.githubusercontent.com/75672785/233619002-33a2875d-1537-46af-84b8-bf768ec1892f.png)
![8](https://user-images.githubusercontent.com/75672785/233619010-98ee3117-67a1-4ba3-a854-3a29d1d9e005.png)

### Creating a JUnit Test case 



4. Method annotated with @Before will be run before each test executes.

```java
package lab8_202001271;

import static org.junit.Assert.*;

import org.junit.Before;
import org.junit.Test;

public class BoaTest {
	
	private Boa jen;
	private Boa ken;

	@Before
	public void setUp() throws Exception {
		//initialization
		jen = new Boa("Jennifer", 2, "grapes");
		ken = new Boa ("Kenneth", 3, "granola bars");
	}
}
```

5. Added private fields for jen and ken in the Boa class.

```java
private Boa jen;
private Boa ken;
```

- The BoaTest class now includes private fields for jen and ken, which are initialized in the setUp method. The testIsHealthy and testFitsInCage methods have also been modified to use these Boa objects for testing.

- It's important to note that the setUp method will be run before each test method, ensuring that any alterations made to the Boa objects during a test won't impact the objects used in other tests.

6. The code has been updated to include additional test cases. These methods are marked with the @Test annotation, indicating that they will be executed by the testing framework. It's important to note that the order in which the tests are run cannot be guaranteed.

```java
package lab8_202001271;

import static org.junit.Assert.*;

import org.junit.Before;
import org.junit.Test;

public class BoaTest {
	
	private Boa jen;
	private Boa ken;

	@Before
	public void setUp() throws Exception {
		//initialization
		jen = new Boa("Jennifer", 2, "grapes");
		ken = new Boa ("Kenneth", 3, "granola bars");
	}
	
	@Test 
	public void testIsHealthy() {
		assertEquals(false,jen.isHealthy());
		assertEquals(true,ken.isHealthy());
	}
	
	@Test 
	public void testFitsInCage() {
		assertEquals(false,jen.fitsInCage(1)); // less than the size of cage
		assertEquals(false,jen.fitsInCage(2)); // equal to the size of cage		
		assertEquals(true,jen.fitsInCage(3)); // greater than the size of cage
	}
}
```

![12](https://user-images.githubusercontent.com/75672785/233619720-ee00738e-7852-4b24-bad8-d45f87482628.png)
![13](https://user-images.githubusercontent.com/75672785/233619726-05d8e3ca-606e-4aa5-a4ba-c38a7b8a95c4.png)


- The newly added test cases involve testing the functionality of two methods in the Boa class. In the first test case, we instantiate two Boa objects with distinct preferred foods, and verify that the isHealthy method returns false for the first object and true for the second object.

- In the second test case, we assess the fitsInCage method by generating three Boa objects with differing lengths, and evaluating whether they are able to fit in cages of varying lengths.

7. Running the two test cases - isHealthy() and fitsInCage()

![14](https://user-images.githubusercontent.com/75672785/233619806-d4fd5839-5614-4264-a63d-c82a6251cbb8.png)

8. Adding a new method to the Boa class

```java
package lab8_202001271;

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
	public int lengthInInches()
	{
		int LengthInInches=this.length*12;
		return LengthInInches;
	}
	
}
```

![15](https://user-images.githubusercontent.com/75672785/233619885-f8cfe8ac-01d2-459f-beee-37b0bfb01925.png)


9. Adding test cases for new methods
```java
@Test
	public void testlengthInInches()
	{
		assertEquals(24,jen.lengthInInches());
		assertEquals(36,ken.lengthInInches());
	}
```

![16](https://user-images.githubusercontent.com/75672785/233619891-a2256b8b-56ca-4751-92b0-2213b0733ecc.png)

Running the 3 test methods:

![17](https://user-images.githubusercontent.com/75672785/233619904-a48d2ff6-a785-4556-93f4-c6862971549f.png)



