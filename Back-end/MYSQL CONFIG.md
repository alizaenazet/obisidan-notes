```jsx
const {Sequelize} = require('sequelize');

const sequelize = new Sequelize({

dialect:'mysql',
host:'127.0.0.1',
port:'3306',
username:"root",
password:"ALIzaenalAbidin110305",
database:"NoteTodoList"
});

  

sequelize.authenticate()
.then(()=> {console.log(`connect succes`); })
.catch((error)=> {console.log(error)});

module.exports = sequelize;
```