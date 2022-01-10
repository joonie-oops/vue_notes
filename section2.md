```
const app = Vue.createApp({
    data() {
        return {
            courseGoal: 'Finish the course and learn Vue!'
        }
    },
})

app.mount('#user-goal');
```
Code above summarizes lesson 13 and lesson 14.


```
<p>Learn more <a :href="vueLink">about Vue</a>.</p>

data() {
        return {
            courseGoal: 'Finish the course and learn Vue!',
            vueLink: 'https://vuejs.org/'
        }
    },
```
Code above summarizes lesson 15.
I did not provide explanations because I thought it would be self-explanatory.

