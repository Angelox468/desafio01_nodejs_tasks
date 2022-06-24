# Correção da function handleCreateNewTask
## Fazer com que a function crie uma nova task com um id random, não permita criar caso o título seja vazio
### Código
  ```tsx
      if (!newTaskTitle) return; // esse if verifica a negação de newTaskTitle fazendo com que não seja possível criar tasks com o titulo vazio 

      const newTask ={ //criação da variável newTask
        id: Math.random(), //ao passar o math.random para o id fazemos com que seja gerado um id aleatório para a task, porém nao a verificação de id iguais
        title: newTaskTitle, //passamos o newTaskTitle no title pois o input seta o titulo escrito como newTaskTitle
        isComplete: false // faz com o isComplete venha desmarcado, para sinalizar que a task ainda nao foi concluída
      }
      setTasks(oldState => [...oldState, newTask]);// pegamos o set task em formato de callback verificando todo o seu status antigo 
      setNewTaskTitle(''); //essa função resta o setNewTaskTitle para que sempre que criada uma task o input fique vazio
  ```

# Correção da function handleCreateNewTask
## Fazer com que essa function altere entre `true` ou `false` o campo `isComplete` de uma task com dado ID
### Código
```tsx
    function handleToggleTaskCompletion(id: number) {
        // Altere entre `true` ou `false` o campo `isComplete` de uma task com dado ID
        const newTasks = tasks.map(task => task.id === id ?{  // pegamos todas as tasks que foram mapeadas onde se a task.id for = ao id  vamos retornar um objeto que sera a nossa nova task, utilizando '...task' para fazer o spreed da task 
          ...task,
          isComplete: !task.isComplete // então aqui pegamos o mesmo objeto que tínhamos alterando apenas a sua propriedade  
        } : task);

        setTasks(newTasks) // aqui estamos passando a nossa variável newTasks onde alteramos a sua propriedade do isComplete
      }
```

# Correção da function handleRemoveTask
## Fazer com que essa function  remova uma task da listagem pelo ID
### código
```tsx
    const filteredtasks = tasks.filter(task => task.id != id); //usamos const filteredtasks = tasks.filter para filtrar todos os outros itens dentro do array sendo elas as que tem o id diferente 
    setTasks(filteredtasks) // usamos o setTasks para passar um novo estado 
```