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

## JUnit tests cases @Before, @BeforeClass annotations

## 1) Crear proyecto, añadir librerias JUnit y JRE

## 2) Definición de etiquetas @Before, @BeforeClass

@BeforeClass: El método al que etiqueta debe ejecutarse antes del resto de los métodos de prueba de la clase.

@Before: El método estático al que etiqueta debe ejecutarse una vez antes del resto de los métodos de prueba de la clase.

## 3) Crear fichero "JUnitTest" 

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

### 4) Ejecutar las pruebas (click derecho > Run As > JUnit Test)

## JUnit test cases more annotations

## 1) Crear proyecto, añadir librerias JUnit y JRE

## 2) Definición de etiquetas

## 3) Crear fichero "JUnitTest" 

```
package es.uca.junit;		

import static org.junit.Assert.assertEquals;				
import static org.junit.Assert.assertFalse;				

import java.util.ArrayList;		

import org.junit.After;		
import org.junit.AfterClass;		
import org.junit.Before;		
import org.junit.BeforeClass;		
import org.junit.Ignore;		
import org.junit.Test;		

public class JUnitTest {				

    private ArrayList<String> list;					

    @BeforeClass		
    public static void m1() {							
        System.out.println("Using @BeforeClass , executed before all test cases ");					
    }		

    @Before		
    public void m2() {					
        list = new ArrayList<String>();					
        System.out.println("Using @Before annotations ,executed before each test cases ");					
    }		

    @AfterClass		
    public static void m3() {							
        System.out.println("Using @AfterClass ,executed after all test cases");					
    }		

    @After		
    public void m4() {					
        list.clear();			
        System.out.println("Using @After ,executed after each test cases");					
    }		

    @Test		
    public void m5() {					
        list.add("test");					
        assertFalse(list.isEmpty());			
        assertEquals(1, list.size());			
    }		

    @Ignore		
    public void m6() {					
        System.out.println("Using @Ignore , this execution is ignored");					
    }		

    @Test(timeout = 10)			
    public void m7() {					
        System.out.println("Using @Test(timeout),it can be used to enforce timeout in JUnit4 test case");					
    }		

    @Test(expected = NoSuchMethodException.class)					
    public void m8() {					
        System.out.println("Using @Test(expected) ,it will check for specified exception during its execution");					

    }		
}
```

## 4) Crear fichero "TestRunner"


