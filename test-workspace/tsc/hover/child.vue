<script setup lang="ts">
/**
 * This is the default model
 */
const defaultModel = defineModel<string>()

/**
 * This is a required model
 */
const requiredModel = defineModel<string>('requiredModel', { required: true })

/**
 * This is a model with a default value
 */
const modelWithDefault = defineModel<string>('modelWithDefault', {
  default: 'default value',
})

/**
 * This is a deprecated model
 * @deprecated This model is deprecated and should not be used
 */
const deprecatedModel = defineModel<string>('deprecatedModel')

const { withDefault = false } = defineProps<{
  /**
   * This is a requird prop
   * @foo This is a custom tag
   */
  requiredProp: string

  /**
   * This is a prop with a default value
   */
  withDefault?: boolean

  /**
   * @description A very long description: Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
   * 
   * @anotherDescription
   * Now with multiple lines!
   * Lorem ipsum
   *
   * @name Some name
   *
   */
  justTags?: string

  noDescription?: boolean

  /**
   * Object type
   */
  withObjectType?: {
    foo: string
    bar: number
  }

  /**
   * With some markdown
   *
   * # Who puts a title in a jsdoc comment?
   *
   * > This is a blockquote
   *
   * - This is a list item
   * - This is another list item
   */
  withMarkdown?: string

  /**
   * With code block
   * ```ts
   * const foo: string = 'bar'
   * ```
   */
  withCodeBlock?: string

  /**
   * This is a deprecated prop
   * @deprecated This prop is deprecated and should not be used
   */
  deprecatedProp?: string

  /**
   * This is a model created without `defineModel`
   */
  manualModel?: string

  onSomePropEvent?: (value: string) => void

  /**
   * This is a model created without `defineModel` and with a prop as an event
   */
  manualModelWithPropEvent?: string

  'onUpdate:manualModelWithPropEvent'?: (value: string) => Promise<void>
}>()

defineEmits<{
  /**
   * This is a custom event
   */
  customEvent: []

  /**
   * This is an event with a payload
   */
  eventWithPayload: [payload: string, payload2: number]

  /**
   * This is a deprecated event
   * @deprecated This event is deprecated and should not be used
   */
  deprecatedEvent: []

  'update:manualModel': [value: string]
}>()

defineSlots<{
  /**
   * This is a default slot
   */
  default(): any

  /**
   * This is a slot with props
   */
  slotWithProps(props: { foo: string }): any

  /**
   * This is a deprecated slot
   * @deprecated This slot is deprecated and should not be used
   */
  deprecatedSlot(): any
}>()

defineExpose<{
  /**
   * This is a method that can be called from the parent component
   */
  exposedMethod: () => void

  /**
   * This is a property that can be accessed from the parent component
   */
  exposedProperty: string
}>()
</script>
