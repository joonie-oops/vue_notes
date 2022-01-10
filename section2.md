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

```
<h2>{{ outputGoal() }}</h2>

methods: {
        outputGoal() {
            const randomNumber = Math.random();
            if (randomNumber < 0.5) {
                return 'Learn Vue!';
            } else {
                return 'Master Vue!';
            }
        }
    }
```
Code above summarizes lesson 16. Here, we introduce methods for the first time.

```
const app = Vue.createApp({
    data() {
        return {
            courseGoalA: 'Finish the course and learn Vue!',
            courseGoalB: 'Master Vue and build amazing apps!',
            vueLink: 'https://vuejs.org/'
        }
    },
    methods: {
        outputGoal() {
            const randomNumber = Math.random();
            if (randomNumber < 0.5) {
                return this.courseGoalA;
            } else {
                return this.courseGoalB;
            }
        }
    }
})

app.mount('#user-goal');
```
Code above summarizes lesson 17 and 18. Basically change data() and outputGoal(). Nothing much to see here.

```
<p v-html="outputGoal()">
```
where outputGoal() returns <h2>Blah Blah Blah...</h2>
This appends h2 as a child element of p.

```
<button @click="add">Add</button>
<button @click="reduce">Remove</button>
<p>Result: {{counter}}</p>

methods: {
    add() {
      this.counter += 1
    },
    reduce() {
      this.counter -= 1
    }
  }
```
Code above summarizes lesson 19~22. I only posted snippets but it should be easy to understand. Basically attach an event listener with @click, write the code in the methods section, and make changes to the counter held in data().

```
<button @click="add(10)">Add 10</button>
<button @click="reduce(5)">Subtract 5</button>

methods: {
    add(num) {
      this.counter += num;
    },
    reduce(num) {
      this.counter -= num;
    }
}
```
Code above summarizes lesson 23.

```
<input type="text" @input="setName">
<p>Your Name: {{ name }}</p>

const app = Vue.createApp({
  data() {
    return {
      counter: 0,
      name: '',
    };
  },
  methods: {
    add(num) {
      this.counter += num;
    },
    reduce(num) {
      this.counter -= num;
    },
    setName(event) {
      this.name = event.target.value;
    }
  }
});
```
I didn't know what snippet to paste so I just pasted the entire code.
This lesson(lesson 24) was taking input from user(in the <input> field, storing that data in the data(), and then outputting that data in a <p></p>
How do you accomplish this?
<input type="text" @input="setName"> invokes the function setName whenever the user types something. The setName(event) then sets up the name. With the changed name in data(), the programmer can freely use it wherever he/she desires.
Okay, that's cool but what if you want to add an argument to setName, such as setName("Park"). This would be problematic because we need the event argument to set the name according to what the user typed. Thankfully, vue provides us with a solution. You can use setName($event, "Park"). Then at setName,
```
setName(event, lastName) {
      this.name = event.target.value + ' ' + lastName ;
    }
```
Tada! It sounds confusing at first but actually it's a piece of cake.


```
<form action="">
    <input type="text">
    <button>Sign Up</button>
</form>
```
Is there a way in Vue to prevent the page from refreshing when the user types on the Sign Up button? Of course there is!
```
<form @submit.prevent="submitForm">
    <input type="text">
    <button>Sign Up</button>
</form>

submitForm(event) {
  alert('Submitted!')
}
```
Sorry for typing the same code twice but here we can see that I put an @submit.prevent which adds a submit event handler and PREVENTS the page from refreshing by addin the .prevent modifier. There are other modifiers such as @click.left, @click.right...
So with this knowledge, let's output confirmedName only when the user types enter in <input> as opposed to each keypress. How could we go about this task? 

```
data() {
    return {
      counter: 0,
      name: '',
      confirmedName: '',
    };
},
```

Add a confirmedName field in data(). The name field updates every single time, but confirmedName updates only after the user types enter.
```
<input type="text" @input="setName" @keyup.enter="confirmInput">
```
As you can see, I added the @keyup.enter="confirmInput" and made sure to run this function only after the user keyups enter.
The input has two event handlers: input & keyup.enter



