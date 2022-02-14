# Research for RBAC validation

## Requirements

1. Independant of Authentication method
2. Link with Graph
3. Different roles per location in the Graph
4. Policy definition through API
5. Query possibilities

## RBAC / ABAC 

https://stackoverflow.com/questions/26594816/how-to-store-rights-alternatives-to-xacml/26599248

### History

In access control you have different models that have come up with time. Historically you first had DAC and MAC. You had the notion of access control lists (also known as identity-based access control or IBAC).

Then suddenly, the sole identity of a user was no longer enough. We started to organize users into roles and groups. That led to the creation of RBAC or role-based access control which NIST formalized into a standard.

### Why RBAC / ABAC
Fast forward 10+ years and roles are not enough anymore. ACLs and RBAC are too user-centric. They do not cater for context or relationships. They are not fine-grained enough. A new model called ABAC or attribute-based access control emerges. NIST is also in the process of standardizing ABAC. ABAC is capable of implementing any type of access control requirement and can cater for user, resource, action, and context attributes.

You can read more on ABAC here: http://csrc.nist.gov/projects/abac/

### XACML and alternatives

So, what about XACML? XACML - the eXtensible Access Control Markup Language - is an implementation of the ABAC model. It is the most widely spread implementation of ABAC. You ask whether there are alternatives. Some that come to mind include:

- SecPal: this is (was?) a Microsoft research initiative. To the best of my knowledge, it is not used outside research.
- Permis is a policy-based access control model. It is not widely spread either.
- Microsoft has its own language for Windows Server called SDDL. You can read more on that from Microsoft.


## Possibilities & candidate libraries

### Gremlin & Cosmos db
https://docs.microsoft.com/en-us/azure/cosmos-db/graph/how-to-use-resource-tokens-gremlin


### Casbin.NET

> Risks: not many contributions recently.

https://github.com/casbin/Casbin.NET

- Enforce the policy in the classic {subject, object, action} form or a customized form as you defined, both allow and deny authorizations are supported.
- Handle the storage of the access control model and its policy.
- Manage the role-user mappings and role-role mappings (aka role hierarchy in RBAC).
- Support built-in superuser like root or administrator. A superuser can do anything without explicit permissions.
- Multiple built-in operators to support the rule matching. For example, keyMatch can map a resource key `/foo/bar` to the pattern `/foo*`.

**Not included**

- Authentication (aka verify username and password when a user logs in)
- Manage the list of users or roles. I believe it's more convenient for the project itself to manage these entities. Users usually have their passwords, and Casbin is not designed as a password container. However, Casbin stores the user-role mapping for the RBAC scenario.

In Casbin, an access control model is abstracted into a CONF file based on the PERM metamodel (Policy, Effect, Request, Matchers). So switching or upgrading the authorization mechanism for a project is just as simple as modifying a configuration. You can customize your own access control model by combining the available models. For example, you can get RBAC roles and ABAC attributes together inside one model and share one set of policy rules.

Relevant link for Hierarchy RBAC: https://casbin.org/docs/en/rbac

### XACML
An old, existing standard.  (SOA timeframe, so might be outdated)
https://en.wikipedia.org/wiki/XACML

### Open Policy Agent 
Upcoming standard, with implementations for different open source runtimes. 
https://www.openpolicyagent.org/

#### Graph example

https://www.openpolicyagent.org/docs/v0.22.0/policy-reference/#graphs

```
package graph_reachable_example

org_chart_data = {
  "ceo": {},
  "human_resources": {"owner": "ceo", "access": ["salaries", "complaints"]},
  "staffing": {"owner": "human_resources", "access": ["interviews"]},
  "internships": {"owner": "staffing", "access": ["blog"]}
}

org_chart_graph[entity_name] = edges {
  org_chart_data[entity_name]
  edges := {neighbor | org_chart_data[neighbor].owner == entity_name}
}

org_chart_permissions[entity_name] = access {
  org_chart_data[entity_name]
  reachable := graph.reachable(org_chart_graph, {entity_name})
  access := {item | reachable[k]; item := org_chart_data[k].access[_]}
}
```

### Scaled Access
A startup of Leuven that offers OPA as a service.
https://www.scaledaccess.com/ 
Contact through Yves Goeleven, if needed

