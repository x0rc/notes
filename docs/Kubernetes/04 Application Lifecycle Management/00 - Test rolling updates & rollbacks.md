# Test rolling updates & rollbacks

The rolling update strategy is **a gradual process that allows you to update your Kubernetes system with only a minor effect on performance and no downtime**. In this strategy, the Deployment selects a Pod with the old programming, deactivates it, and creates an updated Pod to replace it.

Max Unavailable value under RollingUpdateStrategy in deployment details shows us up to how many PODs can be down for upgrade at a time.

![[Pasted image 20220628102736.png]]

25% of 4 = 1