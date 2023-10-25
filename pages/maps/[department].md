---
sources:
- france.sql
---


# {$page.params.department}

<BigValue data={france.filter(d => d.department === $page.params.department)} value="sales" title="Sales" subtitle="in USD" />


