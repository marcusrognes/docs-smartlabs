---
title: Meteor actions
permalink: /docs/meteor-actions/
---

### Basic setup

Single action setup

```

export const actionName = {
	name: 'namespace.actionName',
	validate(args){
		check(args, {
			someId:String,
			data:{
				someData: String
			}
		});
	},
	/**
	* Runs on both the client and server
	*/
	run(args){
		/**
		* Check if user is logged in
		*/
		if (!this.userId) {
			throw new Meteor.Error(this.name + '.authentication', 'notAuthenticated');
		}

        return Collection.update(args.someId, {
        	$set:args.someData
        });
	},
	/**
    * Runs only on the client side, this is what actually invokes the method call.
    */
	call(args, callback){
		const options = {
			returnStubValue: true,
			throwStubExceptions: true
		};

		Meteor.apply(this.name, [args], options, callback);
	}
};

/**
* Registers the meteor method
*/
Meteor.methods({
    [actionName.name]: function (args) {
        actionName.validate.call(this, args);
        return actionName.run.call(this, args);
    }
});

```
