# DoublyLinkedList

> 
    const DoublyLinkedList = function() {
        this.head = null
        this.tail = null
        this.length = 0
    }
    DoublyLinkedList.prototype = {
        constructor: DoublyLinkedList,
        _Node(element) {
            return {
                element,
                prev: null,
                next: null
            }
        },
        insertAt(element, position) {
            if (position < 0 || position > this.length) {
                return false
            }
            let node = this._Node(element)
            if (position === 0) {
                node.next = this.head
                this.head.prev = node
                this.head = node
            } else if (position === this.length) {
                node.prev = this.tail
                this.tail.next = node
                this.tail = node
            } else {
                let index = 0
                let current = this.head
                while (index++ < position) {
                    current = current.next
                }
                let prev = current.prev
                let next = current
                prev.next = node
                node.prev = prev
                node.next = next
                next.prev = node
            }
            this.length++
            return true
        },
        removeAt(position) {
            if (position < 0 || position >= this.length) {
                return null
            }
            let current
            if (position === 0) {
                current = this.head
                if (this.length === 1) {
                    this.tail = null
                } else {
                    this.head = current.next
                    this.head.prev = null
                }
            } else if (position === this.length - 1) {
                current = this.tail
                this.tail = current.prev
                this.tail.next = null
            } else {
                let index = 0
                while (index++ < position) {
                    current = current.next
                }
                let prev = current.prev
                let next = current.next
                prev.next = next
                next.prev = prev
                current.prev = current.next = null
            }
            this.length--
            return current.element
        }
    }