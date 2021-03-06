Supervision services
====================

MORSE exposes several services to remotely manage and monitor the simulator.

These services are automatically exposed on a socket interface, on port 4000.

All these services belongs to a virtual component called ``simulation`` and
follows the normal syntax for socket requests.  Thus, a request to retrieve the
list of robots would look like that::

  > telnet localhost 4000
  Connected to localhost.
  > req1 simulation list_robots
  req1 OK ['Robot1', 'Robot2']


Available services
------------------

- ``list_robots`` (no parameter): returns the list of the robots currently
  available in the simulation
- ``reset_objects`` (no parameter): reset the position of all objects in the
  simulation (in other word, restart the simulation)
- ``quit`` (no parameter): quit the game mode and so terminate the simulation
- ``activate`` (component_name): Activate the functionality of the specified component
- ``deactivate`` (component_name): Deactivate  the functionality of the specified component
- ``suspend_dynamics`` (no parameter): suspend the physics at the game engine
  level
- ``restore_dynamics`` (no parameter): enable again the physics at the game
  engine level
- ``details`` (no parameter): returns a structure containing the details about
  the simulation currently running, including the list of robots, the list of
  services and datastreams, ...
- ``set_log_level`` ``cmpnt`` (string) ``level`` (string): changes the
  level of logging for the component ``cmpnt`` to the level ``level``.
- ``get_scene_objects`` (no parameter): returns an hierarchical dictionary
  structure of all objects in the scene along with their positions and
  orientations (as quaternion).
- ``set_object_visibility`` ``cmpnt`` (string) ``visible`` (bool): make the
  object referenced by ``cmpnt`` visible or invisible (it still exists at
  physic level)
- ``set_object_dynamics`` ``cmpnt`` (string) ``state`` (bool): enable or
  disable the dynamics (physics) associated to component ``cmpnt``.

.. note::
  Simulation services are stored in :py:mod:`morse.core.supervision_services`.
