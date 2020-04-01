# Promise

// 以下两行其实是做的同样的事情 \[func1, func2\].reduce\(\(p, f\) =&gt; p.then\(f\), Promise.resolve\(\)\); Promise.resolve\(\).then\(func1\).then\(func2\);

