# BinarySearchTree

> 
    const BinarySearchTree = function() {
        this.root = null
    }
    BinarySearchTree.prototype = {
        constructor: BinarySearchTree,
        _Node(key) {
            return {
                key,
                left: null,
                right: null
            }
        },
        getRoot() {
            return this.root
        },
        insert(key) {
            let node = this._Node(key)
            const insertNode = (node, newNode) => {
                if (newNode.key < node.key) {
                    if (node.left === null) {
                        node.left = newNode
                    } else {
                        insertNode(node.left, newNode)
                    }
                } else {
                    if (node.right === null) {
                        node.right = newNode
                    } else {
                        insertNode(node.right, newNode)
                    }
                }
            }
            if (this.root === null) {
                this.root = node
            } else {
                insertNode(this.root, node)
            }
        },
        remove(key) {
            const removeNode = (node, key) => {
                if (node === null) {
                    return null
                }
                if (key < node.key) {
                    node.left = removeNode(node.left, key)
                    return node
                } else if (node.key < key) {
                    node.right = removeNode(node.right, key)
                    return node
                } else {
                    if (node.left === null && node.right === null) {
                        return null
                    }
                    if (node.left === null) {
                        return node.right
                    } else if (node.right === null) {
                        return node.left
                    }
                    let minNode = findMinNode(node)
                    node.key = minNode.key
                    node.right = removeNode(node.right, minNode)
                    return node
                }
            }
            const findMinNode = (node) => {
                if (node === null) {
                    return null
                }
                while (node && node.left) {
                    node = node.left
                }
                return node
            }
            this.root = removeNode(this.root, key)
        },
        min() {
            const findMin = (node) => {
                if (node === null) {
                    return null
                }
                while (node && node.left) {
                    node = node.left
                }
                return node.key
            }
            return findMin(this.root)
        },
        max() {
            const findMax = (node) => {
                if (node === null) {
                    return null
                }
                while (node && node.right) {
                    node = node.right
                }
                return node.key
            }
            return findMax(this.root)
        },
        search(key) {
            const search = (node, key) => {
                if (node === null) {
                    return false
                }
                if (key < node.key) {
                    return search(node.left, key)
                } else if (node.key < key) {
                    return search(node.right, key)
                }
                return true
            }
            return search(this.root, key)
        },
        inOrderTraverse(callback) {
            const inOrderTraverse = (node, callback) => {
                if (node) {
                    inOrderTraverse(node.left, callback)
                    callback(node.key)
                    inOrderTraverse(node.right, callback)
                }
            }
            inOrderTraverse(this.root, callback) 
        },
        preOrderTraverse(callback) {
            const preOrderTraverse = (node, callback) => {
                if (node) {
                    callback(node.key)
                    preOrderTraverse(node.left, callback)
                    preOrderTraverse(node.right, callback)
                }
            }
            preOrderTraverse(this.root, callback)
        },
        postOrderTraverse(callback) {
            const postOrderTraverse = (node, callback) => {
                if (node) {
                    postOrderTraverse(node.left, callback)
                    postOrderTraverse(node.right, callback)
                    callback(node.key)
                }
            }
            postOrderTraverse(callback)
        }
    }
    ;(() => {
        let tree = new BinarySearchTree()
        tree.insert(10)
        tree.insert(5)
        tree.insert(12)
        tree.insert(15)
        tree.insert(2)
        tree.inOrderTraverse((key) => {
            console.log(key)
        })
        console.log(tree.min())
        console.log(tree.max())
        console.log(tree.search(20))
    })()