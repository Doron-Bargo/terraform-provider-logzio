# Authentication Groups Provider

Provides a Logz.io authentication groups resource. This can be used to create and manage Logz.io authentication groups.

* Learn more about authentication groups in the [Logz.io Docs](https://docs.logz.io/api/#tag/Authentication-groups)

**Note:** one authentication groups will manage all authentication groups. If you'll create a new resource it will override
the existing authentication groups.

## Example Usage

```hcl
resource "logzio_authentication_groups" "my_auth_groups" {
	authentication_group {
		group = "group_testing_1"
		user_role = "USER_ROLE_ACCOUNT_ADMIN"
	}
	authentication_group {
		group = "group_testing_2"
		user_role = "USER_ROLE_REGULAR"
	}
	authentication_group {
		group = "group_testing_3"
		user_role = "USER_ROLE_READONLY"
	}
}
```

## Argument Reference

* `authentication_group` - (Block List) Sets details for the authentication groups. Must be at least one `authentication_group` in a resource.

#### Nested schema for `authentication_group`:

* `group` - (String) Name of authentication group.
* `user_role` - (String) User role for that group. Can be one of the following: `USER_ROLE_ACCOUNT_ADMIN`, `USER_ROLE_REGULAR`, `USER_ROLE_READONLY`.

##  Attribute Reference
* `manage_groups_id` - (Int) Id for the resource, generated by the provider. It has no real use outside of Terraform.

## Importing resource:

The import command expects an id for the import command, but the authentication groups api does not work with ids.
Because of that, if you wish to import authentication groups, you can use whichever numeric id you'd like.
That id won't affect anything, it will only be the id of the resource in Terraform.

```bash
terraform import logzio_authentication_groups.imported 1234
```