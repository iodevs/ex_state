# ExState ![](https://github.com/catchcake/ex_state/workflows/Continuous%20Integration/badge.svg)

Elixir [finite state machines](https://en.wikipedia.org/wiki/Finite-state_machine) and [statecharts](http://www.inf.ed.ac.uk/teaching/courses/seoc/2005_2006/resources/statecharts.pdf) library.

- Adheres to the [SCXML specification](https://www.w3.org/TR/scxml/).
- Inspired by [XState JS](https://xstate.js.org/docs/).

## Quick start

### Install
```elixir
def deps do
  [
    {:ex_state, "~> 2.0.1"}
  ]
end
```

### Usage

```elixir
  iex> definition = %{
  iex>   id: "toggle",
  iex>   initial: :inactive,
  iex>   states: %{
  iex>     inactive: %{
  iex>       on: %{
  iex>         TOGGLE: %{
  iex>           target: :active
  iex>         }
  iex>       }
  iex>     },
  iex>     active: %{
  iex>       on: %{
  iex>         TOGGLE: %{
  iex>           target: :inactive
  iex>         }
  iex>       }
  iex>     }
  iex>   }
  iex> }
  iex> machine = ExState.machine(definition)  # and now create state machine
  iex> ExState.transition(machine, :TOGGLE)  # and transit to new state
  %ExState.Machine{
    context: nil,
    id: "toggle",
    initial: :inactive,
    options: %ExState.Options{actions: nil, guards: nil},
    state: %ExState.State{
      context: nil,
      event: %ExState.Event{data: nil, type: :TOGGLE},
      value: :active
    },
    states: %{
      active: %ExState.NodeType.Atomic{
        on: %{
          TOGGLE: %ExState.Transition{actions: [], cond: nil, target: :inactive}
        }
      },
      inactive: %ExState.NodeType.Atomic{
        on: %{
          TOGGLE: %ExState.Transition{actions: [], cond: nil, target: :active}
        }
      }
    }
  }
```

## Statecharts?

Statecharts are a formalism for modeling stateful, reactive systems. This is useful for declaratively describing the behavior of your application, from the individual components to the overall application logic.

- [Statecharts - A Visual Formalism for Complex Systems](http://www.inf.ed.ac.uk/teaching/courses/seoc/2005_2006/resources/statecharts.pdf) by David Harel
- [The World of Statecharts](https://statecharts.github.io/) by Erik Mogensen
- [Pure UI](https://rauchg.com/2015/pure-ui) by Guillermo Rauch
- [Pure UI Control](https://medium.com/@asolove/pure-ui-control-ac8d1be97a8d) by Adam Solove
- [Spectrum - Statecharts Community](https://spectrum.chat/statecharts)

## License

> TODO: Add license
