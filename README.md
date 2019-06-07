<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" 
          content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />

    <title>Mini App</title>

    <style>
      
      div.user-photo {
        margin: 1em auto;
        width: 150px;
        height: 150px;
        border-radius: 50%;
        overflow: hidden;
      }
      
      body {
        background-color: white;
      }
      
      .select{
        margin: 2.5em;
      }
      
      .details{
        color: white;
        background-color: #6200ee;
        font-size: 1.3em;
        margin-top: 4em;
        padding: 0.5em 1em 0.5em 1em;
      }
      
      .details p{
        margin: 0.3em;
      }
      
      #outcome{
        position: absolute;
        right: 2.2em;
        bottom: 6.5em;
        width: 100px;
        text-align: center;
      }
      
      #outcome h5{
        padding: 1em;
        background-color: white;
        border-radius: 10%;
        margin: 0%;
      }
      
      #outcome p{
        height: 40px;
        color: white;
        border-bottom: 5px solid white;
        font-size: 2em;
        margin: 0%;
        padding: 0.5em 0em 0.5em 0em;
      }
      
      #oracle{
        margin-top: 2.5em;
        border: 1px solid;
        width: 100%;
      }        
        
    </style>
  </head>
  <body>
    <button id="filter-query" class="mdc-icon-button material-icons">filter_list</button>
    <div class="select">
      <select class="select-text">
        <option selected="true" disabled="disabled">Select User</option>
      </select>
    </div>
    <div class="user-photo">
      <img src="https://via.placeholder.com/150" alt="user">
        </div>
        <div class="details mdc-elevation--z3">
          <p>
            <span class="prop" data-age="Age:"></span>
            <span class="value" data-age-value></span>
          </p>
          <p>
            <span class="prop" data-height="Height:"></span>
            <span class="value" data-height-value></span>
          </p>
          <p>
            <span class="prop" data-weight="Weight:"></span>
            <span class="value" data-weight-value></span>
          </p>
          <p>
            <span class="prop" data-gender="Gender:"></span>
            <span class="value" data-gender-value></span>
          </p>
          <p>
            <span class="prop" data-country="Country:"></span>
            <span class="value" data-country-value></span>
          </p>
    </div>
    
    <button id="oracle" class="mdc-button">Calculate BMI</button>
          
    <div id="outcome">
      <h5 class="mdc-typography--headline5">BMI</h5>
      <p></p>
    </div>
      
    <script>
      const users = [];
      const countries = [
                         'chad',
                         'sierra leone',
                         'mali',
                         'gambia',
                         'uganda',
                         'ghana',
                         'senegal',
                         'somalia',
                         'ivory coast',
                         'isreal',
        ];
      
      const computeBMI = ({weight,height,country}) =>{
        const newHeight = height*0.3048;
        const bmi = (weight/(newHeight^2));
        const newBmi = bmi * 0.82;
        const check = countries.find(state => state === country);
        const finalBmi = check ? newBmi : bmi;
        return finalBmi.toFixed(1);
      }
      
      const getSelectedUser = (userId)=>{
        return users.find(({id}) => id == userId);
      }
      
      const displaySelectedUser = ({target})=>{
        const user = getSelectedUser(target.value);
        const properties = Object.keys(user);
        
        const properties.forEach(prop => {
          const element1 = document.querySelector('span[data-${prop}]');
          const element2 = document.querySelector('span[data-${prop}-value]');
          if (element1){
            element1.textContent = prop;
            element2.textContent = user[prop];
          }
        })
      };
      
      const letsCalculateBMI = () => {
        const element = document.querySelector('.select-text').value;
        const user = getSelectedUser(element.value);
        
        const bmi = computeBMI(user);
        const pTag = document.querySelector('#outcome p');
        pTag.textContent = bmi;
      };
      
      const powerupTheUI = () => {
        const button = document.querySelector('#oracle');
        button.addEventListener("change", displaySelectedUser);
        
        const select = document.querySelector('.select-text');
        select.addEventListener("click", letsCalculateBMI);
      };
      
      const displayUsers = (users) =>{
        users.forEach((user)=> {
          let value = document.createElement('option');
          value.setAttribute('value', user.id);
          value.textContent = user.name;
          document.querySelector('.select-text').appendChild(value);
        });
      }
      
      const fetchAndDisplayUsers = () => {
        users.push({
          age: 40,
          weight: 75,
          height: 6,
          country: 'Nigeria',
          name: 'Charles Odili',
          id: 'dfhb454768DghtF'
        });
      }
          age: 37,
          weight: 70,
          height: 6,
          country: 'Nigeria',
          name: 'Oluwasomidotun Odumosu',
          id: 'dhgs283674DsgcL'
      });
      
      displayUsers(users);
      };
      
      const startApp = () => {
        powerupTheUI();
        fetchAndDisplayUsers();
      };

      startApp();
    </script>
  </body>
</html>
