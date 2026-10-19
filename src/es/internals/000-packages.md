# 000 — Paquetes

El equipo de Yii3 dividió el framework en varios paquetes que cumplen con
los siguientes acuerdos.

Para todos los paquetes, el nombre del repositorio de GitHub coincide
exactamente con el nombre del paquete de Packagist.

Para obtener una lista completa de paquetes y su estado de compilación,
consulta la [página de estado en
yiiframework.com](https://www.yiiframework.com/status/3.0).

## Paquetes específicos de Yii (framework y extensiones)
    
- nombrados como `yiisoft/yii-something` o más específicos:
  `yii-type-something` e.j.:
    - módulos: `yii-module-users`, `yii-module-pages`
    - temas: `yii-theme-adminlte`, `yii-theme-hyde`
    - widgets: `yii-widget-datepicker`
    - ...
- titulados como "Yii Framework ..."
- pueden tener cualquier dependencia y código específico de Yii

## Paquetes de propósito general (bibliotecas)
  
- puedes usarlos independientemente del Framework Yii
- nombrados como `yiisoft/something` sin el prefijo yii
- titulados como "Yii ..."
- no deben tener dependencias de ningún paquete específico de Yii
- deberían tener el menor número de dependencias posible

## Configuraciones y valores por defecto

Lo siguiente aplica tanto a paquetes específicos de Yii como a paquetes de
propósito general:

- El paquete puede tener un directorio `config` con valores por defecto
  específicos de Yii.
- El paquete puede tener "config-plugin" en la sección "extra" de
  `composer.json`.
- El paquete no debe tener dependencias en la sección `require` de
  `composer.json` que se usen solo en `config`.
- Debes namespaeear los parámetros con `vendor/package-name`:

```php
return [
    'vendor/package-name' => [
        'param1' => 1,
        'param2' => 2,
    ],
];
```
  
## Versiones

Todos los paquetes siguen la versionado [SemVer](https://semver.org/):

- `x.*.*` - cambios incompatibles en la API.
- `*.x.*` - añadir funcionalidad (compatible hacia atrás).
- `*.*.x` - correcciones de errores (compatible hacia atrás).

La primera versión estable debe ser 1.0.0.

El número de versión de cada paquete no depende de la versión de ningún otro
paquete o del nombre/versión del framework, solo en su propio contrato
público.  El framework en su conjunto tiene el nombre "Yii3".

Está bien usar paquetes con diferentes versiones mayores juntas, siempre que
sean compatibles.

## Soporte de versiones de PHP

The support of PHP versions supported for a package depends on [PHP versions
life cycle](https://www.php.net/supported-versions.php).

- Package versions with active support MUST support all PHP versions that
  have active support.
- Both packages and application templates MUST have supported versions that
  receive bug and security fixes.  These SHOULD correspond to PHP versions
  receiving security fixes.
- Packages and application templates MIGHT have supported versions that work
  with unsupported PHP versions.
- Bumping the minimal PHP version in a package or an application template is
  a minor change.

## composer.json

A logical OR operator in version ranges MUST use double pipe (`||`). For example: `"yiisoft/arrays": "^1.0 || ^2.0"`.   
