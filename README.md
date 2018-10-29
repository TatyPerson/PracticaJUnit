# Práctica con JUnit

## Descargar & Instalar JUnit

### 1) Descargar Eclipse Neon (4.6) (Eclipse IDE for Java EE Developers)

https://www.eclipse.org/downloads/packages/release/neon/3/eclipse-ide-java-ee-developers

### 2) Crear proyecto, añadir librerías JUnit y JRE

### 3) Crear clase java "TestJUnit.java"

```
package es.uca.junit;
   
import org.junit.Test;
import static org.junit.Assert.assertEquals;
public class TestJunit {
   @Test
   public void testSetup() {
      String str= "I am done with Junit setup";
      assertEquals("I am done with Junit setup",str);
   }
}
```

### 4) Crear clase java "TestRunner.java" para ejecutar las pruebas

```
package es.uca.junit;

import org.junit.runner.JUnitCore;
import org.junit.runner.Result;
import org.junit.runner.notification.Failure;

public class TestRunner {
   public static void main(String[] args) {
      Result result = JUnitCore.runClasses(TestJunit.class);
      for (Failure failure : result.getFailures()) {
         System.out.println(failure.toString());
      }
      System.out.println("Result=="+result.wasSuccessful());
   }
} 
```

### 5) Ejecutar las pruebas (click derecho > Run As > JUnit Test)

## JUnit tests cases @Before, @After annotations

## 1) Crear proyecto, añadir librerias JUnit y JRE

## 2) Crear fichero "JUnit Test" 

```
package es.uca.junit;
import static org.junit.Assert.*;
import java.util.ArrayList;
import org.junit.*;


public class JUnitTest {
    private ArrayList testList;
    
            @BeforeClass
            public static void onceExecutedBeforeAll() {
                System.out.println("@BeforeClass: onceExecutedBeforeAll");
            }
            
            @Before
            public void executedBeforeEach() {
                testList = new ArrayList();
                System.out.println("@Before: executedBeforeEach");
            }

            @Test
            public void EmptyCollection() {
                assertTrue(testList.isEmpty());
                System.out.println("@Test: EmptyArrayList");
            }

            @Test
            public void OneItemCollection() {
                testList.add("oneItem");
            assertEquals(1, testList.size());
                System.out.println("@Test: OneItemArrayList");
            }
}
```

### 2) Ejecutar las pruebas (click derecho > Run As > JUnit Test)
