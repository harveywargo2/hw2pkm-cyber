## References
- https://docs.blusapphire.io/use-cases/sigma-rules/understanding-sigma-rule
- 
Rules
- https://sigmahq.io/docs/basics/rules.html
- https://github.com/SigmaHQ/sigma

SIGMA Taxonomy
- https://github.com/SigmaHQ/sigma-specification/blob/main/Taxonomy_specification.md

Guides
- https://socprime.com/blog/sigma-rules-the-beginners-guide/
- https://docs.blusapphire.io/sigma-rules/understanding-sigma-rule

Converters
- https://sigconverter.io/

Search Engine
- https://sigmasearchengine.com/

## General
- Generic and open signature format that allows you to describe relevant log events
- Standard repo for open source detections
- Yara for logs stored in yaml

## Rule Yaml
```
title:
id:
status:
description:
author:
references:
tags:
logsource:
category:
product:
detection:
selection:
filter:
condition:
falsepositives:
level:

```

## Minimum Fields
```
title:
description:
references:
logsource:
category:
product:
detection:
selection:
condition:

```