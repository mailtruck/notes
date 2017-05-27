> http://stackoverflow.com/questions/11692860/how-can-i-efficiently-download-a-large-file-using-go

I'll assume you mean download via http (error checks omitted for brevity):

```

import ("net/http"; "io"; "os")
...
out, err := os.Create("output.txt")
defer out.Close()
...
resp, err := http.Get("http://example.com/")
defer resp.Body.Close()
...
n, err := io.Copy(out, resp.Body)

```
The http.Response's Body is a Reader, so you can use any functions that take a Reader, to, e.g. read a chunk at a time rather than all at once. In this specific case, io.Copy() does the gruntwork for you.