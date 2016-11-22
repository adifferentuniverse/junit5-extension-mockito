A simple JUnit 5 extension to integrate Mockito into JUnit 5 tests somewhat simpler.

The `MockitoExtension` showcases the `TestInstancePostProcessor` and `ParameterResolver`
extension APIs of JUnit 5 by providing dependency injection support at the field level
and at the method parameter level via via Mockito 2.x's `@Mock` annotation.

Example Usage:

    import static org.junit.jupiter.api.Assertions.assertEquals;
    import static org.mockito.Mockito.when;
    
    import org.junit.jupiter.api.BeforeEach;
    import org.junit.jupiter.api.Test;
    import org.junit.jupiter.api.extension.ExtendWith;
    import org.mockito.Mock;
    import com.example.Person;
    import com.example.mockito.MockitoExtension;
    
    @ExtendWith(MockitoExtension.class)
    class MyMockitoTest {
    
        @BeforeEach
        void init(@Mock Person person) {
            when(person.getName()).thenReturn("Dilbert");
        }
    
        @Test
        void simpleTestWithInjectedMock(@Mock Person person) {
            assertEquals("Dilbert", person.getName());
        }
    
    }


See also:

- [Mockito issue #390](https://github.com/mockito/mockito/issues/390)
- [Mockito issue #438](https://github.com/mockito/mockito/issues/438)
- [Mockito issue #445](https://github.com/mockito/mockito/issues/445)
