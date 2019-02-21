### execa
---
https://github.com/sindresorhus/execa

```js
const execa = require('execa');

(async () => {
  const {stdout} = await execa('echo', ['unicorns']);
  console.log(stdout);
})();


const execa = require('execa');

(async () => {
  execa('echo', ['uniconrs']).stdout.pipe(process.stdout);
  
  const {stdout} = await execa.shell('echo unicorns');
  
  try {
    await execa.shell('exit 3');
  } catch (error) {
    console.log(error);
    /*
    {
      message: 'Command failed: /bin/sh -c exit 3'
      killed: false,
      code: 3,
      signal: null,
      cmd: '/bin/sh -c exit 3',
      stdout: '',
      stderr: '',
      timedOut: false
    }
    */
  }
})();

try {
  execa.shellSync('exit 3');
} catch (error) {
  console.log(error);
  /*
  {
    message: 'Command failed: /bin/sh -c exit 3'
    code: 3,
    signal: null,
    cmd: '/bin/sh -c exit 3',
    stdout: '',
    stderr: '',
    timeOut: false
  }
  */
}

const execa = require('execa');
const getStream = require('get-stream');

const stream = execa('echo', ['foo']).stdout;

stream.pipe(process.stdout);

getStream(stream).then(value => {
  console.log('child output:', value);
});
```

```
npm install execa
```

```
```


