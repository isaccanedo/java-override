# 1. Visão Geral
Neste tutorial rápido, veremos como usar a anotação @Override.

# 2. @Override Annotation
Em uma subclasse, podemos substituir ou sobrecarregar métodos de instância. Substituir indica que a subclasse está substituindo o comportamento herdado. Sobrecarga é quando uma subclasse está adicionando um novo comportamento.

Às vezes, sobrecarregaremos por acidente quando realmente pretendíamos substituir. É fácil cometer este erro em Java:

```
public class Machine {
    public boolean equals(Machine obj) {
        return true;
    }

    @Test
    public void whenTwoDifferentMachines_thenReturnTrue() {
        Object first = new Machine();
        Object second = new Machine();
        assertTrue(first.equals(second));
    }
}
```

Surpreendentemente, o teste acima falha. Isso ocorre porque esse método equals está sobrecarregando Object # equals, não o substituindo.

Podemos usar a anotação @Override em métodos herdados para nos proteger desse erro.

Neste exemplo, podemos adicionar a anotação @Override acima do método equals:

```
@Override
public boolean equals(Machine obj) {
    return true;
}
```

Neste ponto, o compilador irá gerar um erro, informando-nos que não estamos substituindo iguais como pensamos.

Então, podemos corrigir nosso erro:

```
@Override
public boolean equals(Object obj) {
    return true;
}
```

Por ser fácil sobrecarregar acidentalmente, é uma recomendação comum usar a anotação @Override em todos os métodos herdados.

# 3. Conclusão
Neste guia, vimos como a anotação @Override funciona em Java.