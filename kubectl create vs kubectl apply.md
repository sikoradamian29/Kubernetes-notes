
#### kubectl create is Imperative, it will create the resource from scratch, but if a resource with given name already exists it will throw an error.

#### kubectl apply is declarative, it will create the resource if it doesn't already exists, but if it exists it will incrementally update it. It will attempt to update it in place whenever possible, performing a "patch" operation to minimize disruption and maintain availability.