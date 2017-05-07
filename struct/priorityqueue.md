# PriorityQueue

> 
    const PriorityQueue = function(){
        this.items = []
    }
    PriorityQueue.prototype = {
        constructor: PriorityQueue,
        _QueueElement(element, priority) {
            return {
                element,
                priority
            }
        },
        enqueue(element, priority) {
            let item = this._QueueElement(element, priority)
            if (this.isEmpty()) {
                this.items.push(item)
            } else {
                let added = false
                let length = this.items.length
                for (let i = 0; i < length; i++) {
                    if (item.priority < this.items[i].priority) {
                        this.items.splice(i, 0, item)
                        added = true
                        break
                    }
                }
                if (!added) {
                    this.items.push(item)
                }
            }
        },
        dequeue() {
            return this.items.pop()
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
    let priorityQueue = new PriorityQueue()
    priorityQueue.enqueue('zxl', 1)
    priorityQueue.enqueue('zfh', 2)
    priorityQueue.print()