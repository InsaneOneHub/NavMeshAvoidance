# Nav Mesh Avoidance
Custom Nav Mesh Avoidance to replace default one. 

![Nav Mesh Avoidance](https://media3.giphy.com/media/cA3Xxd4CnB9TBoIMtG/giphy.gif)

This is simple avoidance implementation to prevent situation when nav mesh agents moving too close to each other. This algorithm is best suitable for average crowds of 10-100 agents. 
Not tested with bigger amounts.

## How to use
First of all, add **Avoidance** component to any GameObject (once). Next, when you spawn any agent, you need to add it to the Avoidance class like this:
```cs
using NavMeshAvoidance;
using UnityEngine;
using UnityEngine.AI;

public class AvoidingAgent : MonoBehaviour
{
  public Avoidance Avoidance;

  void Start()
  {
    var agent = GetComponent<NavMeshAgent>();

    Avoidance.AddAgent(agent);
  }
}
```

And now it will work with avoidance of others agents. 

You also can disable default avoidance. In this case agents will sometimes move through each other, but in priority for them will be to avoid others. Idea of disabling default avoidance is better navigation without "friction", which can be noticed when using default avoidance and 2 or more agents try to move through other one.

When destroying any agent, dont forget to remove it from avoidance too:

```cs
Avoidance.RemoveAgent(agent);
```

## Ordering and Formation
Basic classes added as controls example for agents groups. You can ignore these scripts if you have your own group controls.

## Example
Check SampleScene to see **Avoidance** work example.
