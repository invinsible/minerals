<template>
    <user-status :iswork="isWork" :tired="tired"/>    
    <base-button type="button" :disabled="isWork || tired >= 39" @some-action="startWork">Собирать</base-button>
    <loot :loot="currentMineral"/>
    <history :historyArray="historyArray"/>    
</template>

<script>
import UserStatus from './components/action/UserStatus.vue';
import Loot from './components/action/Loot.vue';
import History from './components/action/History.vue';

function getRandom(min, max) {
  min = Math.ceil(min);
  max = Math.floor(max);
  return Math.floor(Math.random() * (max - min + 1)) + min;
}

export default {
    components: {
        UserStatus,
        Loot,
        History        
    },
    data() {
        return {
            minerals: [
                {
                    id: '01',
                    name: 'Гранит',
                    uri: 'granit',
                    chance: 50
                },
                {
                    id: '02',
                    name: 'Кварц',
                    uri: 'kwarc',
                    chance: 30
                },
                {
                    id: '03',
                    name: 'Малахит',
                    uri: 'malahit',
                    chance: 20
                },
                {
                    id: '04',
                    name: 'Алмаз',
                    uri: 'almaz',
                    chance: 10
                }
            ],            
            isWork: false,
            currentMineral: null,
            tired: 0,
            historyArray: [],
            
            interval: 0,
        }
    },

    watch: {
       tired(value) {
          if(value > 0) {
              this.interval = setTimeout(() => {
                  this.tired -= 3;                  
              }, 10000);
          }
       },
       isWork(value) {
           if(value) {
               clearInterval(this.interval)
           }
       }       
    },

    methods: {
        
        startWork() {
            if(this.tired === 39) {
                console.log('вы слшком устали');
                return
            }

            this.currentMineral = null;
            this.isWork = !this.isWork;

            setTimeout(() => {
                this.isWork = false;
                this.tired += 3;
                this.randomChoose();
            }, 2000);
        },

        randomChoose() {
            let isDropRand = getRandom(1, 4);
            let date = new Date();
            let normalDate = date.getHours() + ':' + date.getMinutes() + ':' + date.getSeconds();

            let historyResult = {
                name: 'Ничего не найдено',
                date: normalDate
            };

            if(isDropRand % 2 === 0) {
                let rand = getRandom(0, this.minerals.length - 1);
                this.currentMineral = this.minerals[rand];

                historyResult.name = this.minerals[rand].name;                
            }
            
            this.pushHistory(historyResult)           
        },

        pushHistory(obj) {
            this.historyArray.push(obj);
        }
    }
}
</script>