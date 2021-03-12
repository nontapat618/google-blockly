<template>
  <div id="app">

    <div id="stage1" class="div-table" >
      <div class="div-table-row">
        <div class="div-table-col-restrict"> <div id="car" class="car" style="width:70px;height:70px;background-color:yellow;position:absolute;"></div> </div>
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-restrict"> </div>
      </div>
      <div class="div-table-row">
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-restrict"> </div>
      </div>
      <div class="div-table-row">
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-available"> </div>
        <div class="div-table-col-available"> </div>
        <div class="div-table-col-available"> </div>
        <div class="div-table-col-available"> </div>
        <div class="div-table-col-available"> </div>
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-restrict"> </div>
      </div>
      <div class="div-table-row">
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-available"> </div>
        <div class="div-table-col-available"> </div>
        <div class="div-table-col-available"> </div>
        <div class="div-table-col-available"> </div>
        <div class="div-table-col-available"> </div>
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-restrict"> </div>
      </div>
      <div class="div-table-row">
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-available"> </div>
        <div class="div-table-col-available"> </div>
        <div class="div-table-col-available">  </div>
        <div class="div-table-col-available"> </div>
        <div class="div-table-col-available"> </div>
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-restrict"> </div>
      </div>
      <div class="div-table-row">
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-available"> </div>
        <div class="div-table-col-available"> </div>
        <div class="div-table-col-available"> </div>
        <div class="div-table-col-available"> </div>
        <div class="div-table-col-available"> </div>
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-restrict"> </div>
      </div>
      <div class="div-table-row">
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-available"> </div>
        <div class="div-table-col-available"> </div>
        <div class="div-table-col-available"> </div>
        <div class="div-table-col-available"> </div>
        <div class="div-table-col-available"> </div>
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-restrict"> </div>
      </div>
      <div class="div-table-row">
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-restrict"> </div>
      </div>
      <div class="div-table-row">
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-restrict"> </div>
        <div class="div-table-col-restrict"> </div>
      </div>

    </div>

    <!-- <BlocklyComponent id="blockly1">
      <block type="controls_ifelse"></block>
      <block type="logic_compare"></block>
      <block type="logic_operation"></block>
      <block type="controls_repeat_ext">
          <value name="TIMES">
              <shadow type="math_number">
                  <field name="NUM">10</field>
              </shadow>
          </value>
      </block>
      <block type="logic_operation"></block>
      <block type="logic_negate"></block>
      <block type="logic_boolean"></block>
      <block type="logic_null" disabled="true"></block>
      <block type="logic_ternary"></block>
      <block type="text_charAt">
          <value name="VALUE">
              <block type="variables_get">
                  <field name="VAR">text</field>
              </block>
          </value>
      </block>
    </BlocklyComponent> -->

    <button @click="playProgram"> Run Program </button>

    <BlocklyComponent id="blockly2" :options="options" ref="foo"></BlocklyComponent>
    <!-- <p id="code">
      <button v-on:click="showCode()">Show JavaScript</button>
      <pre v-html="code"></pre>
    </p> -->
  </div>
</template>

<script>

import BlocklyComponent from './components/BlocklyComponent.vue'
import './blocks/stocks';
import './prompt';

import BlocklyJS from 'blockly/javascript';
import Blockly from 'blockly';
var $ = require('jquery');
var moveItX = 0;
var moveItY = 0;
var finalDirection = '';

// $.fn.animateRotate = function(angle, complete) {
//   return this.each(function() {
//     var $elem = $(this);

//     $({deg: 0}).animate({deg: angle}, {
//       duration: 3,
//       easing: 1,
//       step: function(now) {
//         $elem.css({
//            transform: 'rotate(' + now + 'deg)'
//          });
//       },
//       complete: complete || $.noop
//     });
//   });
// };

export default {
  name: 'app',
  components: {
    BlocklyComponent
  },
  data(){
    return {
      code: '',
      maze: [],
      kuy: 'kuy',
      carPosition: {
        row: null,
        column: null,
      },
      options: {
        media: 'media/',
        grid:
          {
            spacing: 25,
            length: 3,
            colour: '#ccc',
            snap: true
          },
        toolbox:
        `<xml>
          <category name="Text" colour="%{BKY_TEXTS_HUE}">
            <block type="move_forward"></block>
            <block type="move_backward"></block>
            <block type="move_left"></block>
            <block type="move_right"></block>

          </category>
        </xml>`
      }
    }
  },
  created() {

    let moveForward = {
    "message0": "Move Up",
    "previousStatement": null,
    "nextStatement": null,
    "colour": 290,
    "tooltip": "",
    "helpUrl": ""
  }

    let moveBackward = {
    "message0": "Move Down",
    "previousStatement": null,
    "nextStatement": null,
    "colour": 290,
    "tooltip": "",
    "helpUrl": ""
  };

    let moveLeft = {
    "message0": "Move Left",
    "previousStatement": null,
    "nextStatement": null,
    "colour": 290,
    "tooltip": "",
    "helpUrl": ""
  };

    let moveRight = {
    "message0": "Move Right",
    "previousStatement": null,
    "nextStatement": null,
    "colour": 290,
    "tooltip": "",
    "helpUrl": ""
  };


  Blockly.Blocks['move_forward'] = {
    init: function() {
      this.jsonInit(moveForward);
    }
  };

  Blockly.Blocks['move_backward'] = {
    init: function() {
      this.jsonInit(moveBackward);
    }
  };

  Blockly.Blocks['move_left'] = {
    init: function() {
      this.jsonInit(moveLeft);
    }
  };

  Blockly.Blocks['move_right'] = {
    init: function() {
      this.jsonInit(moveRight);
    }
  };

  Blockly.JavaScript['move_forward'] = function() {
    return 'forward\n';
  };

  Blockly.JavaScript['move_backward'] = function() {
    return 'backward\n';
  };

  Blockly.JavaScript['move_left'] = function() {
    return 'left\n';
  };

  Blockly.JavaScript['move_right'] = function() {
    return 'right\n';
  };


  },
  mounted: function() {
    var stage1Table = document.getElementById('stage1');
    for(let i=0; i < stage1Table.children.length; i++) {
      this.maze[i] = [];
      for(let j=0; j < stage1Table.children[i].children.length; j++) {
        let el =  stage1Table.children[i].children[j];
        this.maze[i][j] = el;
        if(i== 4 && j ==4) {
          this.carPosition.row = i;
          this.carPosition.column = j;
        }
      }
    }


  },
  methods: {
      showCode() {
        this.code = BlocklyJS.workspaceToCode(this.$refs["foo"].workspace);
      },
      playProgram() {
        let code = BlocklyJS.workspaceToCode(this.$refs["foo"].workspace);
        let commands = code.split('\n');

        commands.forEach(async (value) =>  {
          await this.moveCar(value);
        });

    },
    async moveCar(value) {
        switch(value) {
            case 'forward':
              finalDirection = 'top';
              moveItX  -= 70;
              break;
            case 'backward':
              finalDirection = 'top';
              moveItX += 70;
              break;
            case 'left':
              finalDirection = 'left';
              moveItY -= 70;
              break;
            case 'right':
              finalDirection = 'left';
              moveItY += 70;
              break;
            default:
              break;
        }    

        if(value == 'forward' || value == 'backward') {
          $('#car').animate({
            opacity: 0.75,
            [finalDirection]: moveItX
          }, 300, function() {
          
          });        
        } else if(value == 'left' || value == 'right') {
          $('#car').animate({
            opacity: 0.75,
            [finalDirection]: moveItY
          }, 300, function() {
          
          });        
        }



        return Promise.resolve(value);
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

html, body {
  margin: 0;
}

#code {
  position: absolute;
  right: 0;
  bottom: 0;
  width: 50%;
  height: 50%;
  margin: 0;
  background-color: beige;
}

#blockly1 {
  position: absolute;
  right: 0;
  top: 0;
  width: 50%;
  height: 50%;
}

#blockly2 {
  position: absolute;
  right: 0;
  bottom: 0;
  width: 50%;
  height: 50%;
}

.div-table {
  display: table;         
  width: auto;         
  background-color: #eee;         
}
.div-table-row {
  display: table-row;
  width: auto;
  clear: both;
}
.div-table-col-restrict {
  float: left; /* fix for  buggy browsers */
  display: table-column;         
  background-color: blue;
  box-shadow: inset 0 0 10px black;

}
.div-table-col-available {
  float: left; /* fix for  buggy browsers */
  display: table-column;         
  background-color: blue;
  box-shadow: inset 0 0 10px black;

}
.div-table-col-test {
  float: left; /* fix for  buggy browsers */
  display: table-column;         
  /* background-color: green; */
}


.div-table-col-restrict,.div-table-col-available,.div-table-col-test {
  width: 70px;         
  height: 70px;
}

img {
  padding: 5px;
  width: 50px;
}
.car{
  position: absolute;
}


/* .move-forward {
  -moz-animation-name: moveforward;
  -moz-animation-duration:1s;
  -moz-animation-timing-function: ease;
  -moz-animation-fill-mode: forwards;
}

@keyframes moveforward {
  from {
    -moz-transform: translate(0);
  }
  to {
    -moz-transform: translate(-65px);
  }
}

.move-back {
  -moz-animation-name: moveBack;
  -moz-animation-duration:1s;
  -moz-animation-timing-function: ease;
  -moz-animation-fill-mode: forwards;
}

@keyframes moveBack {
  0% {
    -moz-transform: translate(0);
  }
  100% {
    -moz-transform: translate(65px);
  }
} 


.move-left {
  -moz-animation-name: moveLeft;
  -moz-animation-duration:1s;
  -moz-animation-timing-function: ease;
  -moz-animation-fill-mode: forwards;
}

@keyframes moveLeft {
  from {
    -moz-transform: rotate(0deg);
  }
  to {
    -moz-transform: rotate(-90deg);
  }
} 

.move-right {
  -moz-animation-name: moveRight;
  -moz-animation-duration:1s;
  -moz-animation-timing-function: ease;
  -moz-animation-fill-mode: forwards;
}

@keyframes moveRight {
  from {
    -moz-transform: rotate(0deg);
  }
  to {
    -moz-transform: rotate(90deg);
  }
}  */


</style>
