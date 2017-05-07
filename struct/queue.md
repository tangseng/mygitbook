# Queue

> 
    const Queue = function(){
        this.items = []
    }
    Queue.prototype = {
        constructor: Queue,
        enqueue(item) {
            return this.items.push(item)
        },
        dequeue() {
            return this.items.shift()
        },
        front() {
            return this.items[0]
        },
        isEmpty() {
            return this.items.length == 0
        },
        size() {
            return this.items.length
        },
        clear() {
            this.items = []
        },
        print() {
            console.log(this.items.toString())
        }
    }
    ;(() => {
        let queue = new Queue()
        queue.enqueue(11)
        queue.enqueue(22)
        queue.print()
        queue.dequeue()
        console.log(queue.isEmpty())
        console.log(queue.size())
        console.log(queue instanceof Queue)
    })()
    //击鼓传花游戏
    const hotPotato = function(gamers, number) {
        let queue = new Queue()
        Array.from(gamers).forEach((gamer) => {
            queue.enqueue(gamer)
        })
        while (queue.size() > 1) {
            for (let i = 0; i < number; i++) {
                queue.enqueue(queue.dequeue())
            }
            console.log(queue.dequeue())
        }
        return queue.dequeue()
    }
    console.log(hotPotato(['zfh', 'zxl', 'zfhaizxl'], 5))