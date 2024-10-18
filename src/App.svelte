<script>
     import Comp1 from "./lib/Comp1.svelte";
     import Comp2 from "./lib/Comp2.svelte";
     import Comp3 from "./lib/Comp3.svelte";
     import Comp4 from "./lib/Comp4.svelte";
     import Comp5 from "./lib/Comp5.svelte";
    // import TopMenu from "./lib/TopMenu.svelte";
  
    // import DetectMessage from "./lib/Detector.svelte";
  
    //Массив объектов, содержащий ссылки на 3 компонента
    const options = [
      { component: Comp1 },
      { component: Comp2 },
      { component: Comp3 },
      { component: Comp4 },
      { component: Comp5 },
    ];
  
    let selected = options[0]; //компонент по умолчанию
    // let active_item = 0;
  
    // /**
    //  * @param {number} idcomp
    //  */
    // function SelectComp(idcomp) {
    //   //Функция вызывается из верхнего меню и определяет
    //   //выбранный пользователем компонент
    //   selected = options[idcomp];
    //   active_item = idcomp;
    // }
  
    // let current_message;
  
    // /**
    //  * @param {string} mess - текст сообщения
    //  */
    // function SendMessage(mess) {
    //   //функция вызывается из компонентов Comp1, Comp2 и Comp3
    //   //Каждый из них формирует свое сообщение, к-е передается
    //   //через аргумент mess  и определяет переменную current_message.
    //   //Current_message передается в компонент Detector через prop messagefrom
    //   current_message = mess;
    //   clicked = true;
    //   setTimeout(() => {
    //     clicked = false;
    //   }, 200);
    // }
  
    // let clicked = false;
    function onclik (id){
      selected=options[id]
    }

  </script>
  
  <main>
    <div class="holy-grail">
      <header>
        <nav>
            <div class='btn' on:click={()=>onclik(0)} >МЕНЮ</div>
            <div class='btn' on:click= {()=>onclik(1)} >ПОГОДА</div>
            <div class='btn' on:click= {()=>onclik(2)} >КУРС РУБЛЯ</div>
            <div class='btn' on:click= {()=>onclik(3)} >НОВОСТИ</div>
            <div class='btn' on:click= {()=>onclik(4)} >ПРОГРАММА ТЕЛЕПЕРЕДАЧ</div>
          
        </nav>
      </header>
  
      <div class="container">
        <div class="left-sidebar">
          <h2>Счастье быть дома</h2>
          <p></p>
        </div>
  
        <div class="main-content">
  
          <!-- Динамические компоненты -->
          <svelte:component
            this={selected.component}
          />
  
        </div>
        <div class="right-sidebar">
          <h2>Правый сайдбар </h2>
          <!-- <DetectMessage messagefrom={current_message} /> -->
           Здесь может быть любая дополнительная информация
        </div>
      </div>
      <footer>
        <p>Подвал</p>
      </footer>
    </div>
  </main>
  
  <style>
    /* Global styles */
    :root {
      font-family: Inter, system-ui, Avenir, Helvetica, Arial, sans-serif;
      line-height: 1.5;
      font-weight: 400;
    }
  
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }
  
    .holy-grail {
      display: flex;
      flex-direction: column;
      min-height: 100vh;
    }
  
    header {
      background-color: #333;
      color: #fff;
      padding: 1em;
      text-align: center;
    }
  
  .btn{
    cursor: pointer;
    background-color: rgb(225, 240, 16);
   border: none;
   color: rgb(37, 36, 126); 
   padding: 15px 32px;
   text-align: center;
   text-decoration: none;
   display: inline-block;
   font-size: 16px;border-radius: 12px;
   font-size: 20px;
   font-style: Georgia;
   font-family: sans-serif;
  }
    .container {
      display: flex;
      flex-wrap: wrap;
      padding: 20px;
      flex: 1;
    }
  
    .left-sidebar {
      flex: 1;
      max-width: 250px;
      margin-right: 20px;
      background-color: #f7f7f7;
      padding: 20px;
    }
  
    .main-content {
      flex: 3;
      padding: 20px;
    }
  
    .right-sidebar {
      flex: 1;
      max-width: 250px;
      margin-left: 20px;
      background-color: #f7f7f7;
      padding: 20px;
    }
  
    footer {
      background-color: #333;
      color: #fff;
      padding: 1em;
      text-align: center;
      height: 50px;
      margin-top: auto;
    }
  
    /* Медиа-запросы - обеспечение респонсивности */
    @media (max-width: 1200px) {
      .left-sidebar,
      .right-sidebar {
        flex: 0 0 200px;
      }
    }
  
    @media (max-width: 992px) {
      .left-sidebar,
      .right-sidebar {
        flex: 0 0 150px;
      }
    }
  
    @media (max-width: 768px) {
      .container {
        flex-direction: column;
      }
      .left-sidebar,
      .right-sidebar {
        max-width: 100%;
        margin: 20px 0;
      }
      .main-content {
        flex: 1;
      }
    }
  
    /* Перенесен в TopMenu */
    /* @media (max-width: 480px) {
    header nav ul {
      flex-direction: column;
    }
    header nav li {
      margin-right: 0;
    }
  } */
  </style>
  
