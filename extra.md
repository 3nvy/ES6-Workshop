> # Extra



especialmente para quem é adepto de programação funcional, é puder usar composição em vez de herança.

Imaginemos o caso seguinte usando `Classes` e `Herança`

<pre>
  <b>Robot</b>
    .conduz()
    
    RobotLimpeza
      .limpa()
      
    RobotAssassino
      .mata()
      
  <b>Animal</b>
    .come()
    
    Cao
      .ladra()
      
     Gato
      .mia()
</pre>

No entanto agora queremos criar uma nova class, um Cao Robot de Limpeza que `conduz()`, `limpa()` e `ladra()`. No entanto não tem um sistema digestivo e por isso não `come()`. Como podemos ver, não conseguimos encaixar o Cão Robot de Limpeza em nenhuma das classes que temos, poderiamos eventualmente criar uma `Class` pai com todos os metodos comuns, mas para alem de não ser bonito, acabariamos com muita informação que nunca iriamos usar.

Usando composição por outro lado, não corremos este risco, uma vez que compomos o nosso Cão Robot de Limpezas com o que ele precisa efectivamente, ao invez de Herdar as suas caracteristicas de outras classes.

<pre>
  //  Conduz()
  const conduz => ({posicao, velocidade}) => ({
    conduzir: () => posicao = posicao + velocidade
  })
  
  //  Limpa()
  const limpa => () => ({
    limpar: () => console.log('A limpar...')
  })
  
  //  Ladra()
  const ladra => ({nome}) => ({
    ladrad: () => console.log('Woof, sou o ${nome}')
  })
  
  //
  const CaoRobotLimpeza = name => {
    let state = {
      nome,
      velocidade: 100,
      posicao: 0
    }
    
    return Object.assign(
      {},
      conduz(state),
      ladra(state),
      limpa()
    )
  }
</pre>
