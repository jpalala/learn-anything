Here's a quick cheat sheet for **Laravel migration column types** and **migration-related Artisan commands**, formatted like a README-style reference.

---

# Laravel Migration Reference

## 🧱 Common Schema Column Types (`$table->...()`)

| Type                                             | Example                              | Notes |
| ------------------------------------------------ | ------------------------------------ | ----- |
| `$table->id()`                                   | Auto-incrementing BIGINT primary key |       |
| `$table->bigIncrements('id')`                    | Manually define big auto ID          |       |
| `$table->increments('id')`                       | INT auto-increment                   |       |
| `$table->integer('age')`                         | Signed integer                       |       |
| `$table->unsignedInteger('age')`                 | Unsigned integer                     |       |
| `$table->bigInteger('views')`                    | BIGINT                               |       |
| `$table->boolean('is_active')`                   | TRUE / FALSE                         |       |
| `$table->string('name', 255)`                    | VARCHAR (default 255)                |       |
| `$table->char('code', 3)`                        | Fixed-length string                  |       |
| `$table->text('description')`                    | TEXT                                 |       |
| `$table->mediumText('content')`                  | MEDIUMTEXT                           |       |
| `$table->longText('bio')`                        | LONGTEXT                             |       |
| `$table->float('rating', 8, 2)`                  | Floating number                      |       |
| `$table->double('amount', 15, 8)`                | Bigger float                         |       |
| `$table->decimal('price', 8, 2)`                 | Decimal                              |       |
| `$table->date('dob')`                            | DATE                                 |       |
| `$table->datetime('published_at')`               | DATETIME                             |       |
| `$table->timestamp('created_at')`                | TIMESTAMP                            |       |
| `$table->timestamps()`                           | created_at + updated_at              |       |
| `$table->softDeletes()`                          | deleted_at                           |       |
| `$table->enum('status', ['draft', 'published'])` | ENUM                                 |       |
| `$table->json('meta')`                           | JSON                                 |       |
| `$table->uuid('uuid')`                           | UUID                                 |       |
| `$table->foreignId('user_id')->constrained()`    | Foreign key                          |       |

---

## ⚙️ Artisan Migration Commands

```bash
php artisan make:migration create_users_table        # Create a new migration
php artisan migrate                                   # Run all pending migrations
php artisan migrate:fresh                             # Drop all tables + re-run all
php artisan migrate:refresh                           # Rollback + re-run
php artisan migrate:rollback                          # Undo last batch
php artisan migrate:reset                             # Rollback all migrations
php artisan migrate:status                            # List migrations
php artisan migrate --seed                            # Migrate + run seeders
php artisan make:model Post -m                       # Make model + migration
```

---

Let me know if you want a **template migration file stub** or **relationship examples**!
