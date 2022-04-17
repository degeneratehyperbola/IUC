# Scriptus

## Intro
... intro, quite literally

Y'know, I like colossal things. I like when I'm beneath this big massive thing that I want to explore so bad, yet struggle to comprehend a bit. Then the relief of finally understanding it all. Arousing. We'd make some huge complex network of things then want it all visualized this instant. And I like this human trait. So here I am, laying in bed, wanting to see all, every single internet node upon my own eyes, perhaps in an image of sorts.

## Research phase
A quick search lead me to an idea of a map based on Hilbert curve with all routable IPv4 addresses on it. ... how it's done briefly ... I quickly adopted this idea.
One attempt was by the Carna botnet back in 2012, pretty cool looking, the other one, quite recent actually, by suckerpinch https://www.youtube.com/watch?v=JcJSW7Rprio, which, totally, did not inspire me in the first place. No more significant successful attemps... until now.
Which brings us to the development stage.

## Development
Here starting from an empty Python file, based on my reflex, discarding it upon realising that I'd need to find a way (or a library) to ping the IPs first. And I found one: icmplib https://pypi.org/project/icmplib/ for Python. The interface is pretty simple. Later I also realised that you can choose the source interface on this thing which is pretty cool.

No I needed a way to iterate through our 3.6 billion routable IPs...
*goofy music starts playing*

... iteration over addresses, optimizations, multiple interfaces, benchmarking, dashboard of info while running the script

... A funny thing was going on with built-in Python range generators. They were slow, like really slow with big numbers. I don't know why, because when I remade the range generator entirely on Python it worked just fine! With the same parameters! I wasn't even going to rebuild them really, this idea was a simple goofy "ahh, it just might fix it". Like what the hell, Python?

... I find it hard to believe that this speed test was created by someone or something that goes by the name of OOKLA...

Now, how do i build this "Hilbert" curve?
https://github.com/measurement-factory/ipv4-heatmap
Here I found a cool repository which is, apparently, supposed to help me map a set of ping results onto a Hilbert curve thing.

# Later needed shit

- 1.0.0.0-10.0.0.0
- 11.0.0.0-100.64.0.0
- 100.128.0.0-120.0.0.0
- 128.0.0.0-169.254.0.0
- 169.255.0.0-172.16.0.0
- 172.32.0.0-192.0.0.0
- 192.0.1.0-192.0.2.0
- 192.0.3.0-192.88.99.0
- 192.88.100.0-192.168.0.0
- 192.169.0.0-198.18.0.0
- 198.20.0.0-198.51.100.0
- 198.51.101.0-203.0.113.0
- 203.0.114.0-224.0.0.0

- 3584817920 IPv4 addresses

## Benchmarks
- 4000 threads
- 1600 pings/sec
- 650000 pings
- 3 interfaces
- no interface shutdowns
- ~622.4 hrs

## Bottlenecks include
- CPU
- Network interfaces
- Tunnel
