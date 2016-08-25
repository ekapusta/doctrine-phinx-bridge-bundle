Doctrine phinx bridge bundle
============================

Auto-generates Phinx migrations from Doctrine scheme differences.


Command arguments
-----------------

*classname* — migration class name to use instead of autogenerated `AutoMigration1234567890`.


Configuration
-------------

Currently uses `doctrine_migrations.dir_name` for path and `doctrine_migrations.table_name` for ignoring migrations table.


Usage
-----

Run `bin/console doctrine:migrations:diff:phinx` to get automigration like `20160825101109_auto_migration20160825131109.php`:

    <?php
    use Phinx\Migration\AbstractMigration;
    class AutoMigration20160825131109 extends AbstractMigration
    {
        public function up()
        {
            $this->execute('CREATE TABLE abc (id INT AUTO_INCREMENT NOT NULL, name VARCHAR(255) NOT NULL, PRIMARY KEY(id)) DEFAULT CHARACTER SET utf8 COLLATE utf8_unicode_ci ENGINE = InnoDB');
        }
        public function down()
        {
            $this->execute('DROP TABLE abc');
        }
    }

Or run `bin/console doctrine:migrations:diff:phinx AddAbcTableMigration` to get your named `20160825101313_add_abc_table_migration.php`:

    <?php
    use Phinx\Migration\AbstractMigration;
    class AddAbcTableMigration extends AbstractMigration
    {
        public function up()
        {
            $this->execute('CREATE TABLE abc (id INT AUTO_INCREMENT NOT NULL, name VARCHAR(255) NOT NULL, PRIMARY KEY(id)) DEFAULT CHARACTER SET utf8 COLLATE utf8_unicode_ci ENGINE = InnoDB');
        }
        public function down()
        {
            $this->execute('DROP TABLE abc');
        }
    }
