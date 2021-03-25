# Green Software Engineering

The 2016 Paris Agreement aims to limit the impact of CO₂ emissions to an
increase of 1.5°C in mean global temperatures in the ideal case, or 2°C at most.
Even if these targets are met, it will result in significant damage to global
ecosystems, loss of habitat, and extinction for many species.

Climate models from the IPCC currently predict we are on target for something
closer to an increase of 3-4°C by 2100, which will render large areas of the
planet uninhabitable.

## What does that mean for me?

There is little we can do as individuals to modify carbon emissions at scale,
but as software developers we are in the privileged position of having an
outsized influence; we can make decisions on behalf of thousands of customers.

If we design our software efficiently, it will use less electricity, and
therefore our customers will release less CO₂ into the air.

## How does that work?

In 2015, the Guardian reported that data centres worldwide emit as much CO₂ as
the entire airline industry, each being responsible for around 2% of global
emissions. Since then data centre usage has doubled, and although there is a
push from some of the larger data centre providers to use more renewable energy,
we can also take responsibility for the energy our software takes to run.

Eliminating server-side application logic in favour of pre-rendering at build
time will reduce the amount of CPU required to serve requests. This reduces
power usage, and therefore CO₂.

If we cannot do that, then we can endeavour to use efficient SSR techniques,
like string concatenation, to reduce CPU use on the server. We can pre-zip
content instead of compressing on the fly, paying for the CPU time to compress
the content just once instead of on every request.

Serverless architectures like Lambda will allow our applications can run in
shared instances, rather than dedicated VMs or containers. This allows data
centres to make more efficient use of their hardware: less CPU, less CO₂.

If we can use less energy, burn less of the planet into the sky, it’s a win for
everyone (including the finance department, as reducing CPU time also means
lower bills from AWS!)

## Client Side Consideration

More efficient client-side code will use less battery on customer devices. This
means the customer does not have to charge their device as often.

Smaller bundles mean we use the radios on the customer device for less time,
which allows the operating system to power them down sooner. Less electricity,
less CO₂.

Implementing _Dark Mode_ will reduce power use in devices with OLED screens.
Enabling it by default will encourage more people to use it and reduce power
even further.

**We can make the green choices.**

For more information, check out the
[Principles of Green Software Engineering](https://principles.green) by
Microsoft's Green Cloud Advocacy Lead Asim Hussain,

[Home](../README.md)
