
class is an object constructor

everything in Python is an object

### Example:

```python3
class Derived_Class_Name(object): # object is a Python base class name
    """This is the docstring of this class. Can be accessed by instance.__doc__"""

    def __init__(this_instance_known_as_self, variable1, variable2, variable3=None): # this is a function, a callable
        """This is another docstring
        Args:
          variable1: description.
          variable2: description.
          variable3: description.
        """
        # Public Data Members
        # The members of a class that are declared public are easily accessible from any part of the program.
        # All data members and member functions of a class are public by default.
        this_instance_known_as_self.variable1 = variable1
        this_instance_known_as_self.variable2 = variable2
        this_instance_known_as_self.variable3 = variable3
        
        # Protected Access Modifier
        # The members of a class that are declared protected are only accessible to a class derived from it.
        # Data members of a class are declared protected by adding a single underscore ‘_’ symbol before the data member of that class.
        this_instance_known_as_self._variable4 = {k: None for k in variable1}
        this_instance_known_as_self._variable5 = None
        
        # Private Access Modifier
        # The members of a class that are declared private are accessible within the class only
        # Private access modifier is the most secure access modifier.
        # Data members of a class are declared private by adding a double underscore ‘__’ symbol before the data member of that class.
        this_instance_known_as_self.__variable6 = None
        this_instance_known_as_self.__variable7 = None
```

```python3
Example = Derived_Class_Name([1], 2)
Example.__dict__
```

```python3
    @property # https://www.programiz.com/python-programming/property
    def embeddings(self):
        """The embeddings dictionary."""
        return self._embeddings

    def train(self, num_iterations=100, learning_rate=1.0, plot_results=True,
              optimizer=tf.train.GradientDescentOptimizer):
        """Trains the model.
        Args:
          iterations: number of iterations to run.
          learning_rate: optimizer learning rate.
          plot_results: whether to plot the results at the end of training.
          optimizer: the optimizer to use. Default to GradientDescentOptimizer.
        Returns:
          The metrics dictionary evaluated at the last iteration.
        """
        with self._loss.graph.as_default():
            opt = optimizer(learning_rate)
            train_op = opt.minimize(self._loss)
            local_init_op = tf.group(
                tf.variables_initializer(opt.variables()),
                tf.local_variables_initializer())
            if self._session is None:
                self._session = tf.Session()
                with self._session.as_default():
                    self._session.run(tf.global_variables_initializer())
                    self._session.run(tf.tables_initializer())
                    tf.train.start_queue_runners()

        with self._session.as_default():
            local_init_op.run()
            iterations = []
            metrics = self._metrics or ({},)
            metrics_vals = [collections.defaultdict(
                list) for _ in self._metrics]

            # Train and append results.
            for i in range(num_iterations + 1):
                _, results = self._session.run((train_op, metrics))
                if (i % 10 == 0) or i == num_iterations:
                    print("\r iteration %d: " % i + ", ".join(
                          ["%s=%f" % (k, v) for r in results for k, v in r.items()]),
                          end='')
                    iterations.append(i)
                    for metric_val, result in zip(metrics_vals, results):
                        for k, v in result.items():
                            metric_val[k].append(v)

            for k, v in self._embedding_vars.items():
                self._embeddings[k] = v.eval()

            if plot_results:
                # Plot the metrics.
                num_subplots = len(metrics)+1
                fig = plt.figure()
                fig.set_size_inches(num_subplots*10, 8)
                for i, metric_vals in enumerate(metrics_vals):
                    ax = fig.add_subplot(1, num_subplots, i+1)
                    for k, v in metric_vals.items():
                        ax.plot(iterations, v, label=k)
                    ax.set_xlim([1, num_iterations])
                    ax.legend()
            return results
```
