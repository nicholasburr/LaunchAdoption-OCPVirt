# YAML Syntax 101: The Standard Language of Infrastructure as Code

**Goal:** Master the industry-standard language for configuration and automation.

## Why Do I Care About YAML?

YAML (YAML Ain't Markup Language) is for modern tools such as Kubernetes, Helm, Ansible and GitHub... use YAML to define what they do. By learning this format, you can define configurations that work across teams and platforms.

## A Few Things to Know About YAML Syntax

To read and write YAML, start with mastering these five core concepts:

1. **Indentation:** The golden rule of structure.
2. **Key-Value Pairs:** How to define settings.
3. **Lists:** How to define collections of items.
4. **Comments:** How to leave notes for humans.
5. **Booleans:** How to toggle settings on and off.

### 1. Indentation (The Golden Rule)

YAML relies entirely on indentation to show structure (nesting). This is what makes it readable but also fragile.

* Use Spaces, Not Tabs: Always use 2 spaces for each level of indentation.
* Align Your Data: Items at the same level must be perfectly aligned vertically.

<!-- end list -->

```yaml
parent_item:
  child_item: value  # Indented 2 spaces
  another_child: value
```

### 2. Key-Value Pairs (Dictionaries)

This is the most common data structure. It connects a name (key) to a value.

* Syntax: `key: value` (There must be a space after the colon).

<!-- end list -->

```yaml
apiVersion: v1beta1
kind: AgentConfig
metadata: 
  name: example
rendezvousIP: 192.168.122.10
```

### 3. Lists (Arrays)

Lists are used when you have multiple items under one key (e.g., a list of packages to install or ports to open).

* Syntax: Use a dash `-` followed by a space.

<!-- end list -->

```yaml
interfaces:
  - name: ens3
    macAddress: 52:54:00:d2:2a:66 
  - name: ens4
    macAddress: 52:54:00:d2:2a:67 
  - name: ens5
    macAddress: 52:54:00:d2:2a:68 
```

### 4. Comments

Comments are for humans. The automation engine ignores them. Use them to explain *why* a config exists.

* Syntax: Start the line (or part of the line) with a hash `#`.

<!-- end list -->

```yaml
# If a value is not specified, one address will be chosen from the static IP addresses.
rendezvousIP: 192.168.122.10

```

### 5. Booleans (True/False)

Used for toggles like "admin access" or "service enabled."

* Valid values: `true`, `false` (Best practice is lowercase).

<!-- end list -->

```yaml
fips: true
```

## Putting It Together (Openshift Context)

Here is how those rules look in an Openshift install config.

```yaml
---                                 # Start of file marker
apiVersion: v1beta1
kind: AgentConfig
metadata: 
  name: example
fips: true
rendezvousIP: 192.168.122.10
interfaces:
  - name: ens3
    macAddress: 52:54:00:d2:2a:66 
  - name: ens4
    macAddress: 52:54:00:d2:2a:67 
  - name: ens5
    macAddress: 52:54:00:d2:2a:68
```

## Troubleshooting Tip

If you get a syntax error, 90% of the time it is indentation.

* Did you use a tab instead of a space?
* Did you forget the space after the colon?
* Are your list dashes aligned?

> **Tools:** Use the Red Hat YAML extension in VSCode to catch these errors automatically while you type.
