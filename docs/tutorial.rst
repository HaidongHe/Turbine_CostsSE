.. _tutorial-label:

.. currentmodule:: turbine_costsse.docs.examples.example


Tutorial
--------

Tutorial for Turbine_CostsSE
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

As an example of Turbine_CostsSE, let us simulate using masses for major wind turbine components for the NREL 5MW Reference Model :cite:`FAST2009` using the overall turbine cost model.  The hub and drivetrain component masses must also be provided and are calculated from Sunderland Model :cite:`Sunderland1993`.  

The first step is to import the relevant files and set up the component.

.. literalinclude:: examples/example.py
    :start-after: # 1 ---
    :end-before: # 1 ---

The turbine cost model relies on the mass inputs of all major turbine components.  These filter down to the individual component models through the rotor, nacelle and tower.

.. literalinclude:: examples/example.py
    :start-after: # 2 ---
    :end-before: # 2 ---


Next, we need to set additional inputs to the model.  The blade number must be known to get the total cost for the blade set; the advanced Boolean for the blade must be set to select which mass-cost curve for the blade to use (normal or advanced blade).  We set this to advanced to be in line with the FAST 5 MW reference model.  The machine rating and boolean flags for onboard crane and offshore project must also be set.  These are used in the determination of costs for auxiliary system components.  Finally, the drivetrain configuration is specified so that the proper gearbox and generator coefficients will be used.  This should always be set to 1 for the current model.

.. literalinclude:: examples/example.py
    :start-after: # 3 ---
    :end-before: # 3 ---


We can now evaluate the cost for the turbine and its components.

.. literalinclude:: examples/example.py
    :start-after: # 4 ---
    :end-before: # 4 ---


We then print out the resulting cost values:

.. literalinclude:: examples/example.py
    :start-after: # 5 ---
    :end-before: # 5 ---

The result is:

>>> The results for the NREL 5 MW Reference Turbine in an offshore 20 m water depth location are:
>>>
>>> Overall rotor cost with 3 advanced blades is $1519510.91 USD
>>> Advanced blade cost is $255145.73 USD
>>> Hub cost is $188237.21 USD
>>> Pitch system cost is $555063.45 USD
>>> Spinner cost is $10773.08 USD
>>>
>>> Overall nacelle cost is $3043115.22 USD
>>> LSS cost is $187016.00 USD
>>> Main bearings cost is $58305.64 USD
>>> Gearbox cost is $667445.08 USD
>>> High speed side cost is $15400.07 USD
>>> Generator cost is $451838.76 USD
>>> Bedplate cost is $148183.38 USD
>>> Yaw system cost is $144978.37 USD
>>>
>>> Tower cost is $1031523.34 USD
>>>
>>> Turbine cost is $6153564.42 USD
>>>

Note that the output for the individual nacelle components do not sum to the overall nacelle cost.  There are additional costs in the overall nacelle assembly including the onboard crane, electronics and controls, HVAC, other miscellaneous hardware and the nacelle cover.

Tutorial for NREL_CSM_TCC
^^^^^^^^^^^^^^^^^^^^^^^^^

As an example of NREL_CSM_TCC, let us simulate using the key turbine configuration parameters of the NREL 5MW Reference Model as was done above.

The first step is to again import the relevant files and set up the component.

.. literalinclude:: examples/example.py
    :start-after: # 6 ---
    :end-before: # 6 ---

The turbine cost model relies on the key turbine configuration parameters.  These filter down to the individual component models through the rotor, nacelle and tower.  The blade number must be known to get the total cost for the blade set; the advanced Boolean for the blade must be set to select which mass-cost curve for the blade to use (normal or advanced blade).  We set this to advanced to be in line with the FAST 5 MW reference model.  The machine rating and boolean flags for onboard crane and offshore project must also be set.  These are used in the determination of costs for auxiliary system components.  The drivetrain configuration is specified so that the proper gearbox and generator coefficients will be used, an onboard crane is selected for the turbine, a basic/modular bedplate, and finally the baseline tower design.

.. literalinclude:: examples/example.py
    :start-after: # 7 ---
    :end-before: # 7 ---


Next, we need to set additional inputs to the model to estimate the rotor forces on the nacelle.  These can be specified directly if the rotor thrust and rotor torque are known.  

.. literalinclude:: examples/example.py
    :start-after: # 8 ---
    :end-before: # 8 ---


We can now evaluate the cost for the turbine and its components.

.. literalinclude:: examples/example.py
    :start-after: # 9 ---
    :end-before: # 9 ---


We then print out the resulting cost values:

.. literalinclude:: examples/example.py
    :start-after: # 10 ---
    :end-before: # 10 ---

The result is:

>>> The results for the NREL 5 MW Reference Turbine in an offshore 20 m water depth location are:
>>> Turbine mass: 728368.02 kg
>>> Turbine cost: $5925727.43 USD

It is also possible to output individual component masses and cost as in the Turbine_CostsSE model.

