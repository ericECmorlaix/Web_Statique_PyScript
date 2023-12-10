---
template: pyscript.html
---

<div>
<py-script>
    print("Hello World")
</py-script>
<br/>
<p><strong>Today is <label id='date'></label></strong></p>
<py-script>
import time
pyscript.write('date', time.strftime('%d/%m/%Y %H:%M:%S'))
</py-script>
<br/>

<py-script>  
    print("Let's evaluate π :")
    def eval_pi(n):
        pi = 2
        for i in range(1,n):
            pi *= 4 * i ** 2 / (4 * i ** 2 - 1)
        return pi
    pi = eval_pi(100000)
    s = "&nbsp;" * 10 + f"π is approximately {pi:.5f}"
    print(s)
</py-script>
<br/>

<div id="hey"></div>
<py-script>
pyscript.write('hey', f'Hey Mate !')
</py-script>
</div>

