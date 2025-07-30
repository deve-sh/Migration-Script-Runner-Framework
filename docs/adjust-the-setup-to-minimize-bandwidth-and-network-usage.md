# Adjust the setup to minimize bandwidth and network usage

This is more of a tip than a requirement like all other parts of this guide.

When you're working with Cloud resources, you're billed for the bandwidth consumed. This is even more of a problem when you're writing scripts that deal with a ton of data that has to go in and out of a database or a million files that have to be read and summarized.

Such scripts also involve heavy network usage which can slow down the process significantly.

To counter this, make a point to run scripts INSIDE the VPC so the whole setup is pretty much treated as a single machine with a superfast internet connection and most cloud providers do not charge for bandwidth transfer within a VPC.

Better yet, libraries published by cloud providers to interact with their services (Think of the official library to work with AWS Aurora or Google Cloud Firestore), automatically detect if they're running inside their dedicated network and optimize for them and send traffic not over the internet but over the private network minimizing latency.
