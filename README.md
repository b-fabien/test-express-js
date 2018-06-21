# test-express-js

.utilisation de let à la place de const pour appeller les middlesware

    let express = require('express');
    let bodyParser = require('body-parser');
    let app = express();

.l’url Todos/all ne match pas avec la nomenclature REST: app.get('/todos,(req,res)=>{res.send(todos);}) suffi pour afficher

    app.get('/todos/all', (req, res) => { res.send(todos);});

.il n y a pas de catch erreur pour la vérification de number alors que tous les ID sont des strings de plus le status renvoi toujours 200 même si l'ID peut ne pas correspondre

    app.put('/todos/:id', (req, res) => { todos[Number(req.params.id)] = req.body; res.sendStatus(200);
    });

.let todos est est tableaux noté en dur qui sert de base de donnée, il aurait été plus pratique de le placer dans un vrai systéme de base de donnée.

    let todos = [{id: 'jkhsdjkf', content: 'review this code'}];

.cette façon d'entrée une nouvelle donnée dans la base est risquée, le math.random() génere des nombre àléatoirement mais n'exclue pas de sortir plusieurs fois le même nombre

     app.post('/todos', (req, res) => {
      todos.push({
        ...req.body,
        id: Math.random().toString(32).slice(2) 
      });
      res.sendStatus(201); 
     });
