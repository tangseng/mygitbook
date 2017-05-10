# promise

> 
    const promise = new Promise((resolve, reject) => {
        setTimeout( _ => {
            let random = Math.random()
            if (random >= 0.5) {
                resolve(random)
            } else {
                reject(new Error('error: ' + random))
            }
        }, 1000)
    })
    promise.then(data => {
        console.log(data)
    }).catch(error => {
        console.log(error)
    })
    //Promise.all
    Promise.all([
        new Promise(resolve => setTimeout(_ => resolve(1000), 1000)),
        new Promise(resolve => setTimeout(_ => resolve(2000), 2000)),
        new Promise(resolve => setTimeout(_ => resolve(3000), 3000))
    ]).then(data => console.log(data))
    //Promise.race
    Promise.race([
        Promise.reject(0),
        Promise.resolve(1)
    ]).then(data => console.log(data))
    .catch(error => console.log('error: ' + error))