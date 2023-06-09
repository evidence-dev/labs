```sql france
select 'Gironde' as department, 1000 as sales
union all
select 'Cantal' as department, 2000 as sales
union all
select 'Loir-et-Cher' as department, 888 as sales
union all
select 'Seine-et-Marne' as department, 485 as sales
union all
select 'Morbihan' as department, 294 as sales
union all
select 'Vendée' as department, 998 as sales
```



# {$page.params.department}

<BigValue data={france.filter(d => d.department === $page.params.department)} value="sales" title="Sales" subtitle="in USD" />


