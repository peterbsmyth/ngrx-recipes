\# Update Many nested Models

\#\# Scenario

Given two models: \`quote\` and \`chapter\` where:

\`\`\`

interface Quote {

  id: string;

  text: string;

  chapter: Chapter;

}



interface Chapter {

  id: string;

  name: string;

}

\`\`\`

On an extisting \`quote\` reducer that uses ngrx/Entity, update all of the quotes' nested chapters.





\#\# Recipe

\`\`\`ts

case ChapterActionTypes.UPDATE\_ONE\_COMPLETE:

      const idsToUpdate = \(state.ids as string\[\]\).filter\(\(id\) =&gt; state.entities\[id\].chapter.id === action.payload.id\);

      const changes = idsToUpdate.map\(id =&gt; \({

        id,

        changes: { chapter: {

          id: action.payload.id,

          name: action.payload.name

        } }

      }\)\);

      return adapter.updateMany\(changes, state\);

\`\`\`

