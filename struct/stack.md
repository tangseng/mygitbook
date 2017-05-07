# Stack

> 
    const Stack = function(){
        this.items = []
    }
    Stack.prototype = {
        constructor: Stack,
        push(item) {
            return this.items.push(item)
        },
        pop() {
            return this.items.pop()
        },
        peek() {
            return this.items[this.items.length - 1]
        },
        size() {
            return this.items.length
        },
        isEmpty() {
            return this.items.length === 0
        },
        clear() {
            this.items = []
        },
        print() {
            console.log(this.items.toString())
        }
    }
    let stack = new Stack()
    stack.push(1)
    stack.push(2)
    stack.print()
    stack.pop()
    stack.print()
    console.log(stack.isEmpty())
    console.log(stack.size())
    console.log(stack instanceof Stack)