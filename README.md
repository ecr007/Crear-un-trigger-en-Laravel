# Crear-un-trigger-en-Laravel

```php

public function up()
{
    DB::unprepared('
        CREATE TRIGGER tr_CM_01_data_insert BEFORE INSERT ON `CM_01_data`
            FOR EACH ROW
            BEGIN
                SET NEW.created_at = CURRENT_TIMESTAMP;
            END
    ');

    DB::unprepared('
        CREATE TRIGGER tr_CM_01_data_update BEFORE UPDATE ON `CM_01_data`
            FOR EACH ROW
            BEGIN
                SET NEW.updated_at = CURRENT_TIMESTAMP;
            END
    ');
}

public function down()
{
    Schema::dropIfExists('CM_01_data');

    //DB::unprepared('DROP TRIGGER tr_CM_01_data_insert');
    //DB::unprepared('DROP TRIGGER tr_CM_01_data_update');
}
```
