
# Prediction Sets / Forecasts

A prediction set is the primary model for storing individual user forecasts within Cultivate Forecasts. A prediction set can contain a single prediction or multiple predictions, depending on the question type. In a prediction market, all prediction sets have a single prediction (a trade). In an opinion pool, prediction sets have one prediction for each answer in the question.

## Prediction Sets List

> Request:

```shell
curl "https://yoursite.cultivateforecasts.com/api/v1/prediction_sets" \
  -H "Authorization: Bearer b95b4f848cd226e55b7a42f6a8e8669350730270f5a91d64b6c70328b0156d75"
```

> Response:

```json
{
  "prediction_sets": [
    {
      "id": 1,
      "membership_id": 2,
      "question_id": 1,
      "created_at": "2015-08-04T00:21:37.141Z",
      "updated_at": "2015-08-04T00:21:37.141Z",
      "comment_id": 123,
      "rationale":  "this will contain a forecast rationale/comment provided by the user.",
      "predictions": [
        {
          "id": 1,
          "answer_id": 1,
          "membership_id": 2,
          "forecasted_probability": "0.5",
          "starting_probability": "0.3333",
          "final_probability": "0.5",
          "made_after_correctness_known": false
        }
      ]
    },
    {
      "id": 50,
      "membership_id": 5,
      "question_id": 2,
      "created_at": "2015-08-04T00:21:40.730Z",
      "updated_at": "2015-08-04T00:21:40.730Z",
      "comment_id": 123,
      "rationale": "this will contain a forecast rationale/comment provided by the user.",
      "predictions": [
        {
          "id": 64,
          "type": null,
          "answer_id": 4,
          "membership_id": 5,
          "forecasted_probability": "0.3333",
          "starting_probability": "0.3333",
          "final_probability": "0.3333",
          "made_after_correctness_known": false
        },
        {
          "id": 65,
          "type": null,
          "answer_id": 5,
          "membership_id": 5,
          "forecasted_probability": "0.3333",
          "starting_probability": "0.3333",
          "final_probability": "0.3333",
          "made_after_correctness_known": false
        },
        {
          "id": 66,
          "type": null,
          "answer_id": 6,
          "membership_id": 5,
          "forecasted_probability": "0.3333",
          "starting_probability": "0.3333",
          "final_probability": "0.3333",
          "made_after_correctness_known": false
        }
      ]
    }
  ]
}
```

### HTTP Request

`GET https://yoursite.cultivateforecasts.com/api/v1/prediction_sets`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
page | 0 | Pagination page number
membership_id | none | Returns predictions for a single membership
question_id | none | Returns predictions for a single question
created_before | none | Returns only prediction sets created before the passed date. Date should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)
created_after | none | Returns only prediction sets created after the passed date. Date should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)


### Attribute Descriptions

Parameter | Type | Description
--------- | ------- | -----------
id | integer | The id of the prediction set
membership_id | integer | The id of the membership that submitted the prediction set
question_id | integer | The id of the question that this prediction set belongs to
rationale | string | The text of the rationale (if any) that the user submitted with the forecast
predictions.id | integer | The id of the prediction
predictions.answer_id | integer | The id of the answer this prediction belongs to
predictions.membership_id | integer | The id of the membership that submitted the prediction
predictions.made_after_correctness_known | boolean | Whether or not the prediction was submitted after the "correctness" of the answer was already known
predictions.forecasted_probability | float | The probability estimate that the user submitted with the forecast
predictions.starting_probability | float | The consensus probability of the answer prior to incorporating this forecast
predictions.final_probability | float | The consensus probability of the answer prior to incorporating this forecast


