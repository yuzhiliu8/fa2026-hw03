## Part 1

> Terraform and Pulumi both keep a *state file*. Why is state necessary at all — why can't the tool just inspect your AWS account and diff it against your configuration? What does `terraform plan` / `pulumi preview` give you that clicking through the AWS console doesn't?

State connects the resources declared in our configuration to the actual resources in AWS by recording their IDs and other tracked information. Inspecting AWS alone cannot reliably tell the tool which resources it manages or distinguish a resource removed from our configuration from an unrelated resource. terraform plan and pulumi preview show the proposed changes before execution, including updates, deletions, and replacements. This lets us review the effects of a change before applying it.


## Part 2

> Both parts deploy a backend that does the same trivial thing, but they ship it completely differently: Part 1 built a container image, pushed it to a registry, and kept a server running behind a load balancer; Part 2 zipped up one source file and let AWS supply the runtime, with nothing running at all between requests. Compare the two on cold start, cost when idle versus under sustained load, and how each one scales. Part 2 needed far less infrastructure — what did you give up to get that, and when would you still choose Part 1's shape?
