# UPGRADE FROM 1.2 TO 1.3

## Mapping changes

### Yaml driver deprecated

The yaml mapping driver has been deprecated and will be removed in 2.0. Please 
switch to using annotations or XML mapping files. The following classes have
been deprecated:
 * `Doctrine\ODM\MongoDB\Mapping\Driver\YamlDriver`
 * `Doctrine\ODM\MongoDB\Mapping\Driver\SimplifiedYamlDriver`

### `id` attribute in XML mappings deprecated

The `id` attribute to denote identifiers in XML mappings has been deprecated and
will be removed in 2.0. Instead, use the new `id` element to map identifiers
instead of mapping them with `field`.

### Same-namespace resolution dropped

With same-namespace resolution, the metadata driver would look for a class of
that name in the same namespace if the given class name didn't contain a
namespace separator (`\`). This has been deprecated and will be dropped instead.
Use fully qualified class names or the `::class` constant instead:

```php
/**
 * @ODM\Document(repositoryClass=UserRepository::class)
 */
class User
{
    /**
     * @ODM\ReferenceMany(targetDocument=Group::class)
     */
    private $groups;
}
```

### `ClassMetadataInfo` class deprecated

The `Doctrine\ODM\MongoDB\Mapping\ClassMetadataInfo` class has been deprecated
in favor of `Doctrine\ODM\MongoDB\Mapping\ClassMetadata` and will be dropped in
2.0.

### XML mappings

 * The `writeConcern` attribute in document mappings has been deprecated and
   will be dropped in 2.0. Use `write-concern` instead.
 * The `fieldName` attribute in field mappings has been deprecated and will be
   dropped in 2.0. Use `field-name` instead.