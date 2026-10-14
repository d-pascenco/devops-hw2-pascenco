# ДЗ 2 - роль postgres (Пащенко Дмитрий)

Роль - roles/postgres, плейбук - postgres.play.yml, логи сделал спецом в ноуте hw2_Пащенко_Дмитрий.ipynb на всякий случай

vm1 это мой ноут, поэтому подключение local. Postgres на порту 5434, тк на 5432 у меня уже стоит другая постгра

```bash
ansible-galaxy collection install -r requirements.yml
ansible-playbook postgres.play.yml
```

пароль от vault в .vault_pass, в git его не кладу
