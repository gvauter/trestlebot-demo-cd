---
x-trestle-comp-def-rules:
  FakeOS:
    - name: sshd_set_client_alive_interval
      description: SSH allows administrators to set a network responsiveness timeout
        interval. After this interval has passed, the unresponsive client will be
        automatically logged out.
x-trestle-rules-params:
  FakeOS:
    - name: sshd_client_alive_interval
      description: SSH idle timeout value in seconds.
      options: '{"default": "300", "5min": "300", "10min": "600", "1min": "60", "15min":
        "900"}'
      rule-id: sshd_set_client_alive_interval
x-trestle-comp-def-rules-param-vals:
  # You may set new values for rule parameters by adding
  #
  # component-values:
  #   - value 1
  #   - value 2
  #
  # below a section of values:
  # The values list refers to the values as set by the components, and the component-values are the new values
  # to be placed in SetParameters of the component definition.
  #
  FakeOS:
    - name: sshd_client_alive_interval
      values:
        - '300'
x-trestle-param-values:
  ac-02.05_odp:
x-trestle-global:
  profile:
    title: Example Using NIST SP 800-53 Rev 5 Controls and SP 800-53A Rev 5 Assessment
      Procedures
    href: trestle://profiles/oscal_to_bash_example/profile.json
  sort-id: ac-02.05
---

# ac-2.5 - \[Access Control\] Inactivity Logout

## Control Statement

Require that users log out when {{ insert: param, ac-02.05_odp }}.

## Control Assessment Objective

users are required to log out when {{ insert: param, ac-02.05_odp }}.

## Control guidance

Inactivity logout is behavior- or policy-based and requires users to take physical action to log out when they are expecting inactivity longer than the defined period. Automatic enforcement of inactivity logout is addressed by [AC-11](#ac-11).

______________________________________________________________________

## What is the solution and how is it implemented?

<!-- For implementation status enter one of: implemented, partial, planned, alternative, not-applicable -->

<!-- Note that the list of rules under ### Rules: is read-only and changes will not be captured after assembly to JSON -->

<!-- Add control implementation description here for control: ac-2.5 -->

SSH allows administrators to set a network responsiveness timeout interval.  After this interval has passed, the unresponsive client will be automatically logged out.

To set this timeout interval, edit the following line in `/etc/ssh/sshd_config` as follows:

```
ClientAliveInterval <sshd_client_alive_interval> 
```


### Rules:

  - sshd_set_client_alive_interval

### Implementation Status: impemented

______________________________________________________________________
