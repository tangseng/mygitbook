# async

> 
    async function asyncFunc() {
        await setTimeout(_ => console.log('await 1000'), 1000)
    }
    asyncFunc()
    //
    (async () => {
        await 1
    })()